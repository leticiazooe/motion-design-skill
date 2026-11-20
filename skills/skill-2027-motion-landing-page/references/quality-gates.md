# Quality Gates — Skill 2027

Use antes de marcar qualquer implementação de motion como concluída. Testes não executados devem ser reportados como **não verificados**.

## P0 — Conteúdo e conversão

- [ ] Título H1, CTA, imagens e informações essenciais aparecem mesmo sem JavaScript.
- [ ] Navegação, WhatsApp/contato e formulário funcionam antes e depois das animações.
- [ ] SEO e markup semântico permanecem íntegros.
- [ ] Nenhum texto fica permanentemente invisível por animation state, refresh no scroll ou erro de hidratação.
- [ ] Links não são cobertos por overlays animados.
- [ ] Nenhuma mudança remove textos/serviços/dados de clientes existentes.

## P1 — Acessibilidade e compatibilidade

- [ ] prefers-reduced-motion remove movimento espacial, parallax e loops não essenciais.
- [ ] Teclado e foco visível operam em accordion, nav, FAQ e formulário.
- [ ] Movimento não é único canal de informação.
- [ ] Mobile 390px: sem overflow horizontal, CTA oculto, touch indisponível ou hover obrigatório.
- [ ] Tablet 768px e desktop 1440px revisados.
- [ ] Fullscreen zoom, flashes e transições vestibulares evitados ou possuem alternativa.
- [ ] Seções pinned não prendem scrolling de pessoas usuárias.
- [ ] Comportamento de scroll reverso e refresh em posições intermediárias estável.

## P1 — Performance de produção

- [ ] LCP, CLS e INP medidos ou explicitamente não medidos.
- [ ] Não alegar nota 100 sem relatório real.
- [ ] Motion não introduz layout shift nem bloqueia renderização inicial.
- [ ] Animações críticas priorizam transform e opacity.
- [ ] Não deixar will-change em dezenas de elementos.
- [ ] Não duplicar bibliotecas de animação no mesmo projeto.
- [ ] Limpeza de listeners, observers, timeouts e ScrollTriggers verificada.
- [ ] Página testada com imagens/fontes reais e throttling mobile quando possível.
- [ ] Builds e consoles sem falhas.
- [ ] Não adicionar vídeo pesado apenas para criar sensação premium.

## P2 — Qualidade de motion

- [ ] Cada animação tem propósito, não é somente decorativa.
- [ ] Personalidade visual coerente com a marca.
- [ ] Uma seção protagonista ou assinatura, sem espetáculo em cada bloco.
- [ ] Easing e duração consistentes.
- [ ] Reveals não atrasam leitura nem interações.
- [ ] Entrada e saída têm relação causal.
- [ ] FAQ e cards parecem o mesmo sistema visual.
- [ ] Mobile simplifica motion de forma intencional.
- [ ] Gradientes entre seções são contínuos e não criam cortes inesperados.

## Registro de evidências

Preencher após implementação real:

| Campo | Valor |
|---|---|
| URL ou ambiente | |
| Branch / commit | |
| Stack / bibliotecas | |
| Arquivos alterados | |
| Build / testes | |
| Lighthouse mobile antes/depois | |
| LCP / CLS / INP | |
| Reduced motion | |
| Desktop / tablet / mobile | |
| Pendências | |

**Regras:** não inventar métricas; diferenças de Lighthouse entre execuções podem ocorrer. Priorizar tendências medidas e Core Web Vitals de campo quando disponíveis. Se não houver acesso ao navegador ou ambiente, explicar a limitação.
