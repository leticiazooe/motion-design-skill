# Implementação: GSAP + ScrollTrigger em React

Estes exemplos são pontos de partida. Antes de usar, conferir a stack, versões, estrutura real e requisitos de SSR/SSG. Para componentes simples, CSS ou Motion pode ser mais leve.

## Instalação quando GSAP ainda não existe no projeto

~~~bash
npm install gsap
~~~

Não instalar uma segunda biblioteca de animação sem necessidade.

## Exemplo React com import dinâmico e limpeza

O HTML inicial permanece visível. O código só anima quando os módulos carregam, o componente está montado e a pessoa não pediu redução de movimento.

~~~jsx
import { useEffect, useRef } from "react";

export default function LandingMotion() {
  const root = useRef(null);

  useEffect(() => {
    let cancelled = false;
    let context;

    async function initializeMotion() {
      if (window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
        return;
      }

      const [{ gsap }, { ScrollTrigger }] = await Promise.all([
        import("gsap"),
        import("gsap/ScrollTrigger"),
      ]);

      if (cancelled || !root.current) return;

      gsap.registerPlugin(ScrollTrigger);

      context = gsap.context(() => {
        const timeline = gsap.timeline({
          defaults: { ease: "power3.out" },
        });

        timeline.from(".js-hero-motion", {
          y: 20,
          autoAlpha: 0,
          duration: 0.65,
          stagger: 0.08,
          clearProps: "transform,opacity,visibility",
        });

        gsap.utils
          .toArray(".js-scroll-reveal", root.current)
          .forEach((element) => {
            gsap.from(element, {
              y: 18,
              autoAlpha: 0,
              duration: 0.55,
              ease: "power3.out",
              clearProps: "transform,opacity,visibility",
              scrollTrigger: {
                trigger: element,
                start: "top 88%",
                once: true,
              },
            });
          });
      }, root);
    }

    initializeMotion().catch((error) => {
      // Conteúdo permanece visível se o JS falhar.
      console.error("Motion initialization failed", error);
    });

    return () => {
      cancelled = true;
      context?.revert();
    };
  }, []);

  return (
    <main ref={root}>
      <section aria-labelledby="hero-title">
        <p className="js-hero-motion">Design com propósito</p>
        <h1 id="hero-title" className="js-hero-motion">
          Uma experiência que comunica
        </h1>
        <p className="js-hero-motion">
          Conteúdo legível mesmo sem animação.
        </p>
        <a className="js-hero-motion" href="#contato">
          Solicitar orçamento
        </a>
      </section>

      <section className="js-scroll-reveal" aria-labelledby="about-title">
        <h2 id="about-title">Sobre</h2>
        <p>Conteúdo real, acessível e indexável.</p>
      </section>

      <section id="contato">
        <h2>Contato</h2>
      </section>
    </main>
  );
}
~~~

### Atenções ao adaptar

- Acessibilidade: se o elemento em foco estiver sendo animado/ocultado, não atrasar ou bloquear navegação por teclado.
- O exemplo usa JS para a animação; o conteúdo **não** começa oculto no CSS. Há uma pequena possibilidade de flash antes da animação: quando isto for um problema de design, adotar uma estratégia de progressive enhancement cuidadosamente testada, nunca deixar conteúdo invisível sem JS.
- O contexto GSAP reverte animações no unmount. Confirmar se outros componentes não animam as mesmas propriedades.
- Ao mudar rota/DOM, reinicializar triggers do componente afetado; evitar ScrollTrigger.refresh indiscriminado em loop.
- No Next.js App Router, marcar o componente como client component e verificar a fronteira server/client.
- Em Astro Islands, hidratar o componente conforme necessidade e manter markup significativo no HTML.

## CSS para microinterações independentes de JS

~~~css
.premium-action {
  transition:
    transform 160ms cubic-bezier(0.22, 1, 0.36, 1),
    background-color 160ms ease,
    border-color 160ms ease;
}

@media (hover: hover) and (pointer: fine) {
  .premium-action:hover {
    transform: translateY(-2px);
  }
}

.premium-action:focus-visible {
  outline: 2px solid currentColor;
  outline-offset: 4px;
}

@media (prefers-reduced-motion: reduce) {
  .premium-action {
    transition-duration: 1ms;
  }
  .premium-action:hover {
    transform: none;
  }
}
~~~

## FAQ sem dependência de JS

~~~html
<details class="faq-item">
  <summary>Como funciona o atendimento?</summary>
  <div class="faq-item__content">
    <p>Descrição objetiva do processo.</p>
  </div>
</details>
~~~

~~~css
.faq-item summary {
  cursor: pointer;
}
.faq-item__content {
  padding-block: 0.75rem 1rem;
}
~~~

Adicionar motion progressivo com cuidado para não quebrar o comportamento nativo de details/summary.

## Depuração

1. Conteúdo invisível? Remover estilos de opacity:0 no CSS inicial; conferir autoAlpha, kill/revert e erros JS.
2. Trigger repetido? Conferir Strict Mode, hooks, re-render, mount/unmount e cleanup.
3. Falso overflow? Conferir translateX, larguras fixas, pinned elements e containers.
4. Scroll quebrando no mobile? Desabilitar pin e parallax nesta viewport.
5. Jank? Verificar traces da Performance panel; reduzir bibliotecas e propriedades custosas.
6. Hero atrasado? Investigar fontes, mídia LCP, CSS e trabalho JS antes de adicionar mais motion.
