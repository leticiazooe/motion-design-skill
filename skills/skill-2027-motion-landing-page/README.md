# Skill 2027 — Motion Landing Page

Habilidade de IA para planejar, implementar e auditar **motion design premium para landing pages**: hero cinematográfico, scroll storytelling, cards, FAQ, microinterações e transições visuais com atenção a performance, SEO, acessibilidade e conversão.

## Arquivos

- [SKILL.md](SKILL.md) — instruções centrais para o agente e fluxo obrigatório.
- [references/motion-system.md](references/motion-system.md) — tokens de timing, easing, decisões e anti-patterns.
- [patterns/landing-page-recipes.md](patterns/landing-page-recipes.md) — dez receitas por seção.
- [implementation/gsap-react.md](implementation/gsap-react.md) — exemplo React/GSAP com import dinâmico, ScrollTrigger e cleanup.
- [references/quality-gates.md](references/quality-gates.md) — checklist P0/P1/P2 e evidências.

## Como utilizar

Habilidades podem ser instaladas em agentes compatíveis com a convenção SKILL.md. Por exemplo, para adicionar as skills publicadas neste repositório ao ambiente de um agente compatível:

~~~bash
npx skills add leticiazooe/motion-design-skill
~~~

A ferramenta pode permitir selecionar a skill específica quando detectar mais de uma. A instalação depende do agente/ambiente usado; **um fork no GitHub não instala automaticamente a skill no ChatGPT**.

## Exemplos de pedidos

- "Ative a Skill 2027 e crie um hero editorial premium com GSAP, respeitando PageSpeed."
- "Aplique a Skill 2027 para padronizar cards, FAQ e CTAs com motion consistente no mobile."
- "Audite a landing page com a Skill 2027. Corrija primeiro o que prejudica LCP, CLS, acessibilidade e CTA."
- "Crie uma experiência scroll-driven, mas não use pinning no mobile e ofereça reduced motion."

## Relação com a habilidade original

A Skill 2027 é **adicional e especializada**. A skill [motion-design](../motion-design/SKILL.md) da LottieFiles permanece no mesmo repositório, preservada, e funciona como referência geral de princípios de movimento.

## Diretrizes de manutenção

- Evitar mudanças que prejudiquem o conteúdo sem JavaScript.
- Atualizar snippets conforme versões reais das bibliotecas adotadas.
- Acrescentar casos de uso de landing pages sem replicar a identidade visual de um cliente para outro.
- Preservar créditos e termos do projeto original.
