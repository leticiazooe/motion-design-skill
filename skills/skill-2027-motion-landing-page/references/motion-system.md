# Motion System — Skill 2027

## Tokens sugeridos, não obrigatórios

Adotar valores da marca quando existirem. Valores iniciais para a personalidade Premium Editorial:

| Token | Faixa | Aplicação |
|---|---|---|
| quick | 120–180 ms | Press, hover, ícones |
| standard | 240–380 ms | Cards, elementos de interface |
| reveal | 450–700 ms | Entrada de seção e conteúdo |
| cinematic | 700–1100 ms | Um elemento protagonista |
| delay-small | 40–80 ms | Stagger curto |
| distance-mobile | 8–16 px | Reveals mobile |
| distance-desktop | 12–28 px | Reveals desktop |
| ease-in | ease-out-cubic ou expo controlado | Entrada, desaceleração |
| ease-out | ease-in-cubic | Saída, aceleração |

Atenção: nomes das funções ease-in/ease-out em código diferem entre bibliotecas; selecionar pela curva efetiva e direção do movimento.

### CSS baseline

~~~css
:root {
  --motion-quick: 160ms;
  --motion-standard: 320ms;
  --motion-reveal: 560ms;
  --motion-ease-enter: cubic-bezier(0.22, 1, 0.36, 1);
  --motion-ease-exit: cubic-bezier(0.55, 0, 1, 0.45);
}

@media (prefers-reduced-motion: reduce) {
  :root {
    --motion-quick: 1ms;
    --motion-standard: 1ms;
    --motion-reveal: 1ms;
  }

  html {
    scroll-behavior: auto;
  }
}
~~~

Não aplicar uma regra global que remova todas as animações indiscriminadamente sem verificar conteúdo, eventos e estados.

## Matriz de escolha

| Necessidade | Solução inicial | Evitar |
|---|---|---|
| Hover/focus | CSS transition | GSAP em cada botão |
| Accordion/FAQ | HTML details/summary + CSS; JS quando necessário | conteúdo fora do fluxo inacessível |
| Hero com sequência | GSAP timeline ou Motion variants | três bibliotecas ao mesmo tempo |
| Scroll reveal simples | IntersectionObserver + CSS ou GSAP já presente | plugin pesado só para um fade |
| Scroll storytelling | GSAP ScrollTrigger | sticky/pin sem fallback mobile |
| Shared layout React | Motion | mutação manual conflitante do DOM |
| Logo/ícone vetorial animado | SVG/CSS ou Lottie leve | grande payload sem justificativa |

## Hierarquia de movimento

1. **Hero**: uma ação principal, até duas secundárias; CTA visível rapidamente.
2. **Seções**: animação curta para destacar mudanças de narrativa.
3. **Interações**: feedback imediato e previsível.
4. **Ambient**: opcional; se não agregar valor, não usar.

Não exigir camadas ambientais em todas as seções. Efeitos discretos frequentemente parecem mais premium.

## Anti-patterns

- Fade-in com opacity:0 permanente antes do JavaScript inicializar.
- Animar LCP em zero visibilidade por muito tempo.
- ScrollTrigger criado repetidamente em re-render React.
- Configuração de will-change permanente em dezenas de elementos.
- Pinned sections em mobile que escondem o formulário ou impedem o scroll.
- Parallax em grandes distâncias causando enjoo ou distração.
- Animação idêntica em todos os headings e cards.
- 100% de Lighthouse anunciado sem execução de auditoria.
- Slider/marquee sem pausa adequada ou sem respeito a reduced motion.
- Hover como única maneira de revelar informações essenciais.
- Layout thrashing ao animar propriedades geométricas em loop.

## Preservação de performance

- LCP: otimizar imagem hero, fontes e CSS crítico; animation não substitui essas etapas.
- CLS: reservar dimensões de mídia, evitar mudanças dinâmicas de layout.
- INP: minimizar JS e trabalho na thread principal, delegar feedback leve a CSS.
- Medir total de bundle extra, main-thread tasks e FPS antes/depois da biblioteca.
- Tratar matchMedia e media queries do viewport sem assumptions sobre dispositivo.
- Vídeo hero: poster, fallback, controles quando aplicáveis e autoplay apenas se permitido/silenciado; não bloquear conteúdo principal.
