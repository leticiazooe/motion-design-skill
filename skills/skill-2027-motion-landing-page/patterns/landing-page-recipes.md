# Landing Page Recipes — Skill 2027

Escolha padrões de acordo com objetivo e marca. Cada receita tem fallback estático e mobile reduzido.

## 1. Hero editorial premium

**Objetivo**: hierarquia clara e sensação cinematográfica sem atrasar CTA.
- Base: título e CTA renderizados/legíveis mesmo com JavaScript desativado.
- Sequência quando JS está pronto: eyebrow → headline (deslocamento 12–24px) → copy (fade + deslocamento 12px) → CTA → mídia (revelação leve).
- Desktop: stagger 60–90ms, título 550–750ms; mídia até 900ms quando não prejudica o LCP.
- Mobile: encurtar distância e duração; dispensar reveal da mídia se já é o LCP.
- Reduced motion: conteúdo visível estático, sem timeline.

**Critério**: CTA localizável imediatamente; nenhum texto fica invisível durante erro de script.

## 2. Scroll reveal em seções

**Objetivo**: indicar mudança de assunto.
- Título em posição normal, transform Y até 24px + opacity.
- Disparar ao entrar no viewport, nunca exigir scroll adicional para a leitura.
- Uma animação por seção ou pequenos grupos; evitar centenas de observers.
- No mobile, 8–16px e duração menor. Em redução de movimento, mostrar tudo.

## 3. Cards premium com microinteração

**Objetivo**: demonstrar interatividade com sobriedade.
- Hover desktop: translação vertical 2–4px + ajuste sutil de background/border.
- Focus-visible com estado claro sem depender de movimento.
- Clique/touch não precisa simular hover.
- Não animar box-shadow pesado em muitos cards; preferir pseudo-elemento de opacity.
- Cards sem link ou ação não devem parecer clicáveis.

## 4. Imagem com máscara / reveal

**Objetivo**: introduzir mídia de maneira editorial.
- Reveal via clipping ou transform de wrapper quando custo medido for aceitável.
- Evitar mascarar imagem hero que determina LCP.
- Reservar dimensões e object-fit para eliminar CLS.
- Mobile: transição simples ou imagem estática.

## 5. Seção Atendimento / Processo

**Objetivo**: explicar etapas e preservar entendimento.
- Linha de progresso segue leitura, não se move sem scroll/ação do usuário.
- Etapas com stagger curto, mas texto acessível sem movimento.
- Ícones relevantes ao tema (sem engrenagens genéricas quando não combinarem).
- Não usar pinned/scroll-jacking por padrão; preferir fluxo normal e semântica de lista ordenada.

## 6. FAQ premium

**Objetivo**: reduzir fricção e permitir scan rápido.
- Preferir details/summary nativo quando possível; manter keyboard/ARIA.
- Animar ícone e container sem interferir no conteúdo nem provocar saltos bruscos.
- Animar altura somente quando medida/arquitetura justificar; evitar height em loop.
- Reduced motion: abrir e fechar sem transição espacial.
- Permitir vários itens abertos ou um único, conforme experiência aprovada; não assumir.

## 7. Depoimentos / Marquee

**Objetivo**: reforçar prova social sem prejudicar leitura.
- Reforçar consentimento, autenticidade e atribuição das avaliações.
- Conteúdo acessível e legível mesmo sem marquee.
- Pausar sob hover/focus quando aplicável e respeitar reduced motion.
- Evitar clones infinitos que duplicam conteúdo acessível, focável ou indexado.
- Nunca esconder a página inteira atrás do carrossel.

## 8. CTA e contato

**Objetivo**: conversão sem atrito.
- O botão precisa funcionar com e sem animação.
- Priorizar contraste, rótulos, telefone/link correto e feedback de formulário.
- Transição de estado com progressão loading → success/error; anunciá-la para leitores de tela.
- Não movimentar formulário durante digitação ou abertura do teclado mobile.

## 9. Transições entre seções e footer

**Objetivo**: continuidade cromática e fechamento visual.
- Preferir composição CSS estática suave quando a transição já funciona bem.
- Se motion necessário, amplitude pequena e sem distorcer layout.
- O rodapé herda o padrão visual do projeto; a skill não redefine dados ou identidade.
- Links, políticas e crédito permanecem acessíveis.

## 10. Scroll storytelling cinematográfico

**Objetivo**: um momento de alto impacto, nunca um obstáculo.
- Escolher só a seção que merece timeline premium.
- Desenhar frames: entrada, desenvolvimento e resolução.
- Escrutinizar alternativas em mobile, teclado e reduced motion.
- Proibir pin que cause travamento, conteúdo inacessível ou scroll excessivo.
- Verificar leitura fora da viewport e retorno pelo scroll reverso.

## Checklist de composição por página

- Um hero com assinatura visual.
- Uma linguagem consistente de reveal em seções secundárias.
- Interações leves nos pontos clicáveis.
- Uma única seção narrativa especial, se realmente necessária.
- Formulário, CTA e rodapé prioritariamente funcionais e estáveis.

Se as animações não melhoram orientação, significado ou percepção da marca, removê-las.
