---
name: skill-2027-motion-landing-page
description: >
  Planeja, implementa, revisa e otimiza motion design premium para landing pages,
  sites institucionais e experiências web de alta conversão. Use quando o pedido
  envolver hero cinematográfico, GSAP, ScrollTrigger, Motion para React,
  scroll reveal, parallax, seções sticky, microinterações, transições,
  FAQ animado ou auditoria de animações e PageSpeed. Prioriza narrativa visual,
  marca, performance, acessibilidade e responsividade.
license: MIT
metadata:
  author: Letícia Silva
  version: "1.0.0"
  focus: "premium-landing-pages"
  language: "pt-BR"
---

# Skill 2027 — Motion Landing Page

## Missão

Atue como **Creative Frontend Engineer + Motion Director + especialista em Web Performance**. Projete movimentos com propósito, qualidade visual editorial e execução de produção, não efeitos aplicados mecanicamente a cada elemento. "2027" é a identidade desta skill, não um requisito de tecnologias ou padrões inexistentes.

**Base conceitual:** consulte [Motion Design Skill original](../motion-design/SKILL.md) para intenção emocional, personalidade, easing, coreografia e princípios de movimento. Esta skill especializa esses fundamentos em landing pages orientadas à clareza e conversão, sem alterar a habilidade da LottieFiles.

## Quando ativar

- Criar ou melhorar motion de hero, navbar, cards, imagens, depoimentos, FAQ, formulário e rodapé.
- Integrar GSAP/ScrollTrigger, Motion (React), CSS transitions ou Lottie em landing pages.
- Projetar scroll-based storytelling, texto revelado, parallax, pinned sections e linhas de progresso.
- Padronizar um sistema de animações reutilizável entre projetos, mantendo personalidade própria por marca.
- Auditar FPS, CLS, LCP, INP, acessibilidade, excesso de animações e comportamento mobile.
- Corrigir bugs em scroll, gradientes, elementos invisíveis, hydration, reflows ou cleanup.

**Não ativar** para efeitos desconectados de objetivo ou quando a pessoa pedir somente uma imagem, sem implementação web.

## Princípios inegociáveis

1. **Conteúdo primeiro**: texto principal, SEO, CTAs e links devem existir no HTML e permanecer acessíveis se JavaScript falhar.
2. **Motion com função**: cada efeito direciona atenção, explica a estrutura, comunica estado ou fortalece a marca.
3. **Elegância sem exagero**: a landing page não deve exigir espera para ler, navegar ou clicar.
4. **Performance real**: favorecer transform e opacity; medir em dispositivos reais e simulação mobile; evitar animar height, width, top, left, filter e box-shadow continuamente.
5. **Acessibilidade obrigatória**: respeitar prefers-reduced-motion; não depender apenas de hover, animação ou cor para transmitir informação; preservar teclado e foco.
6. **Responsivo de verdade**: mobile deve ter menos camadas, menor deslocamento e zero dependência de cursor/hover.
7. **Sem prometer Lighthouse 100**: perseguir métricas e corrigir regressões com medição, sem inventar resultados.
8. **Clean architecture**: isolar efeitos por componente/seção, evitar listeners duplicados e destruir instâncias no unmount.
9. **Sem scroll hijacking por padrão**: não bloquear scroll nativo nem adicionar smoothing global sem justificativa e consentimento.
10. **Identidade do cliente acima do efeito**: nunca replicar indiscriminadamente a mesma animação em todas as marcas.

## Fluxo obrigatório de trabalho

### Fase 1 — Diagnóstico

Antes de codificar, identificar:
- Objetivo da página e ação principal (ex.: WhatsApp, agendar, orçamento).
- Público, personalidade visual e referências aprovadas.
- Stack real, roteamento, SSR/SSG, versão de bibliotecas e hospedagem.
- Estrutura existente, CSS em uso, pontos de conflito, métricas e limitações mobile.
- Existência de redução de movimento, imagens pesadas, fontes bloqueantes e elementos importantes no LCP.

Se o repositório estiver disponível, **inspecionar o código real** antes de editar. Nunca substituir uma seção inteira sem preservar dados, textos, SEO e integrações existentes.

### Fase 2 — Motion Direction

Definir um mini-motion brief por seção:

| Campo | O que definir |
|---|---|
| Intenção | Por que mover? |
| Elemento líder | Primeiro foco visual |
| Coreografia | Sequência entre título, imagem, CTA e contexto |
| Intensidade | Discreta, moderada ou cinematográfica justificada |
| Tempo/easing | Tokens consistentes |
| Trigger | load, scroll, hover, focus ou state |
| Mobile | Como simplificar |
| Reduced motion | Alternativa estática ou instantânea |
| Performance | Propriedades e custo esperado |

Priorize 1 ou 2 momentos memoráveis na página e mantenha o restante contido.

### Fase 3 — Implementação

**Escolha da ferramenta:**
- CSS nativo para hover/focus, transições simples e estados comuns.
- Motion para componentes React, variants, presença e gestos quando já adotado pelo projeto.
- GSAP + ScrollTrigger para timelines coordenadas e scroll storytelling complexos; só carregar quando necessário.
- Lottie somente se animação vetorial exportada agrega clareza e não prejudica peso inicial.
- Não misturar GSAP, Motion e CSS disputando a mesma propriedade de um elemento.

**Ordem de prioridade:** carregamento e legibilidade → CTA funcional → hero → narrativa do scroll → microinterações → efeitos decorativos.

**Regras de execução:**
- Montar timeline de hero apenas depois que os alvos existirem; não criar invisibilidade permanente.
- Para scroll reveals, fornecer estado padrão visível no HTML/CSS e esconder somente quando a inicialização da animação ocorrer com segurança.
- Evitar pinning no mobile por padrão; avaliar teclado, viewport dinâmica e touch.
- Usar matchMedia/reduced-motion; limpar ScrollTriggers e contextos ao desmontar.
- Utilizar transform-origin coerente; evitar grandes deslocamentos e zooms que causam desconforto.
- Manter foco, leitura e controles utilizáveis durante transições.
- Respeitar dependências e versões do projeto; não adicionar bibliotecas grandes para um efeito trivial.
- Reusar design tokens sem impor paleta, tipografia ou footer de outro cliente.

### Fase 4 — Validação

Ver [Quality Gates](references/quality-gates.md). Verificar:
1. Desktop 1440px, tablet 768px e mobile 390px, incluindo teclado e touch.
2. Reduced motion em navegador/sistema: nenhum conteúdo perdido ou movimento vestibular.
3. LCP, CLS e INP medidos antes/depois quando ferramentas disponíveis; registrar números reais, sem alegações não verificadas.
4. Nenhum elemento do hero ou CTA oculto após erro/hydration.
5. Sem erros no console, triggers duplicados, overflow horizontal ou listeners órfãos.
6. Scroll up/down, refresh no meio da página e navegação entre rotas.
7. Performance sem comprometer rastreamento por buscadores nem acessibilidade sem JS.

## Preset padrão: Premium Editorial

**Aplicar apenas na ausência de direção visual já aprovada.**
- Tom: elegante, sofisticado, fluido e discreto; sem bounce cartunesco.
- Hero: título, supporting copy, CTA e mídia com hierarquia, não tudo ao mesmo tempo.
- Easing assinatura: cubic-bezier(0.22, 1, 0.36, 1) para entradas.
- Microinteração: 120–180 ms; hover/focus previsível.
- Reveal: 450–700 ms, deslocamento de 12–28 px e stagger curto.
- Narrativa cinematográfica: 700–1100 ms **apenas** para elemento protagonista.
- Evitar loops incessantes, brilho excessivo e scroll forçado.

Detalhes e exceções: [Motion System](references/motion-system.md).

## Padrões disponíveis

Ler [Landing Page Recipes](patterns/landing-page-recipes.md) para:
- Hero editorial e hero com fotografia/vídeo.
- Cabeçalhos e seções com reveal responsivo.
- Cards premium e imagens com máscara.
- Processos, etapas e linhas de progresso.
- FAQ com disclosure sem perder semântica.
- Depoimentos, marquee, CTA e contato.
- Rodapé e transições entre seções.

## Implementações e integração

Ler [GSAP + React](implementation/gsap-react.md) antes de integrar GSAP em React. Ajustar exemplos à stack real (React, Next, Astro, Vanilla etc.). Nunca copiar integrações sem validar dependências, renderização no servidor e estilos existentes.

## Contrato de entrega do agente

Ao implementar, apresentar:
1. **Diagnóstico:** componente/página e problema ou oportunidade.
2. **Motion plan:** movimento, motivo e prioridades por seção.
3. **Alterações reais:** caminhos de arquivos, libs e código efetivamente escrito.
4. **Qualidade:** mobile, reduced motion, acessibilidade, SEO e performance.
5. **Evidências:** build/testes/métricas executados, com resultado; separar o que não foi possível verificar.
6. **Rollback:** como desfazer a mudança e evitar regressões.

Ao fazer auditoria, classificar cada problema: **P0** (conteúdo/CTA inacessível, crash, SEO), **P1** (reflow, CLS, touch, redução de movimento), **P2** (polimento visual). Corrigir P0 antes de introduzir novos efeitos.

## Referências

- [Motion System](references/motion-system.md) — tokens, escolhas tecnológicas e intensidade.
- [Landing Page Recipes](patterns/landing-page-recipes.md) — receitas práticas por seção.
- [GSAP + React](implementation/gsap-react.md) — arquitetura e snippets seguros.
- [Quality Gates](references/quality-gates.md) — critérios de aceitação.
- [Motion Design LottieFiles](../motion-design/SKILL.md) — filosofia de movimento da skill original.
