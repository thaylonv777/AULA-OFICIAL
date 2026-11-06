# Padrão de campanhas — PORTAL SÃO LEOPOLDO

Conta de anúncios: **630414970078093**
Negócio: Portal Do Primeiro Imovel (business_id `1937839136294574`)
Nicho: imóveis (venda de casas/apartamentos + captação de corretores)

Levantado direto da conta em 06/11/2026, a partir das campanhas **ativas** (consideradas o padrão atual — o histórico de campanhas pausadas mostra a evolução da nomenclatura ao longo do tempo, não é o modelo a seguir).

---

## 1. Dois tipos de campanha nessa conta

### A) "ROLETA" — Geração de leads (compradores)
Objetivo real: captar lead de quem quer comprar imóvel.

- **Objective**: `OUTCOME_LEADS`
- **Optimization goal**: `LEAD_GENERATION`
- **Destination**: `ON_AD` (formulário nativo do Facebook/Instagram, não site)
- **Billing event**: `IMPRESSIONS`
- **Nome da campanha**: `[ROLETA][<LOCAL>][<CÓDIGO>][SISTEMA PORTAL]`
  - Exemplos reais: `[ROLETA][SL-APE][SISTEMA PORTAL]`, `[ROLETA][CASAS SL][SISTEMA PORTAL]`, `[ROLETA][CANOAS][APARTAMENTOS][SISTEMA PORTAL]`
  - `SL` = São Leopoldo. Local sempre abreviado ou por extenso, seguido do tipo de imóvel (APE/CASAS/APARTAMENTOS) quando relevante.

### B) "CAPTAÇÃO CORRETOR" — Recrutamento de corretores
Objetivo real: atrair corretor pra trabalhar com a Portal, não cliente comprador.

- **Objective**: `OUTCOME_ENGAGEMENT`
- **Optimization goal**: `CONVERSATIONS`
- **Destination**: `WHATSAPP`
- **Nome da campanha**: `[CAPTAÇÃO CORRETOR][<NOME DO RESPONSÁVEL>]`
  - Exemplos: `[CAPTAÇÃO CORRETOR][WILLIAM]`, `[CAPTAÇÃO CORRETOR][MAURO]`

---

## 2. Estrutura de conjuntos (ad sets)

### Campanhas ROLETA: sempre 2 conjuntos
| Conjunto | Nome | Direcionamento |
|---|---|---|
| Aberto | `[CONJUNTO][AB][POS MAN]` | Sem interesses — só geo + idade |
| Interesse | `[CONJUNTO][INT][POS MAN]` | Geo + idade + interesses de imóveis |

`AB` = Aberto, `INT` = Interesse, `POS MAN` = Posicionamento Manual (sempre no nome, sinaliza que não é Advantage+ Placements).

> O usuário mencionou um terceiro conjunto padrão (**interesse + relacionamento**) para venda de imóveis — não encontrado nas campanhas ativas atuais desta conta. Pode ser um padrão de outra conta/cliente, ou não estar em uso aqui no momento. **Confirmar com o usuário.**

### Campanhas CAPTAÇÃO CORRETOR: 1 conjunto só
`[CONJUNTO]` — sem segmentação por interesse, perfil mais amplo (idade 18-35, só geo).

---

## 3. Direcionamento (confirmado via API, usado de verdade)

**Idade**: 18–45 (ROLETA) / 18–35 (CAPTAÇÃO CORRETOR)

**Localização**: cidade inteira (ex: São Leopoldo, city key `269726`) OU raio customizado em km ao redor de um ponto (ex: Canoas, 6km de raio) — varia por campanha/bairro-alvo. `location_types`: `home` + `recent` (às vezes `frequently_in` também).

**Advantage+ Audience**: **sempre desativado** (`advantage_audience: 0`) em toda campanha ativa — bate 100% com a regra fixa já registrada no `CLAUDE.md` da conta MANU2. É padrão confirmado em múltiplas contas/nichos, não coincidência.

**Interesses usados (conjunto `[INT]`)** — nicho "primeiro imóvel":
| ID | Interesse |
|---|---|
| `6003174415534` | Comprador de primeiro imóvel (imóveis) |
| `6004160449695` | Primeira casa (imóveis) |
| `6007114546664` | Subsídio para compra da primeira casa (imóveis) |

---

## 4. Posicionamento

**Campanhas ROLETA** (`POS MAN` no nome — manual, restrito):
- `publisher_platforms`: facebook, instagram
- `facebook_positions`: feed, story, facebook_reels, profile_feed
- `instagram_positions`: stream, story, reels
- Fora: Marketplace, Audience Network, Messenger, WhatsApp (como superfície), Search

**Campanhas CAPTAÇÃO CORRETOR**: posicionamento automático (Advantage+ Placements), sem restrição manual — diferente do padrão ROLETA. **Confirmar se é intencional** (plausível: campanha de recrutamento tem público pequeno/específico, abrir posicionamento pode ajudar a entregar volume).

---

## 5. Criativos e nomenclatura de anúncios

**Nome do anúncio**: `[TIPO][SUBTIPO] LOCAL`
- `[IMG]` ou `[VID]` = formato do criativo
- `[AP]` / `[CASA]` = tipo de imóvel (apartamento/casa), quando aplicável
- `SAOLEO` = sufixo de local (sem espaço, maiúsculo)
- Exemplos reais: `[VID][AP]SAOLEO`, `[VID][CASA]SAOLEO`, `[IMG]`, `[VID] SAOLEO`

Vários anúncios (mesmo nome) dentro do mesmo conjunto = teste de variação de criativo (A/B informal), prática comum nessa conta.

**Call to Action**:
- ROLETA (lead nativo): `APPLY_NOW`
- CAPTAÇÃO CORRETOR (WhatsApp): `WHATSAPP_MESSAGE`

**Título do criativo**: sempre curto e direto — `"FALE CONOSCO"` (ROLETA) ou `"Converse conosco"` (CAPTAÇÃO CORRETOR).

**Estilo de copy (texto principal)** — padrão identificado:
1. Gancho de dor com emoji (ex: "não aguenta mais pagar ALUGUEL", "sair da casa dos pais")
2. Promessa/benefício em lista com ✅ ou bullet
3. CTA direto na última linha ("Clica AGORA pra falar com um especialista")
4. Uso pesado de emoji, caixa alta pontual pra ênfase (não o texto todo)

**Páginas usadas** (IDs confirmados, nomes não resolvidos — conta não dá acesso de listagem a essas páginas de cliente):
- `1377779648743330` → página usada em todas as campanhas ROLETA (leads de compradores)
- `367358306468189` → página usada em CAPTAÇÃO CORRETOR (recrutamento)
São páginas diferentes por finalidade, não a mesma página pra tudo.

---

## 6. Orçamento

Orçamento por conjunto (ABO, não CBO): **R$13 a R$14/dia** por conjunto nas campanhas ROLETA ativas. Bid strategy: `LOWEST_COST_WITHOUT_CAP` (autobid, não vi bid cap manual nas ativas).

---

## 7. Checklist pra replicar esse padrão numa campanha nova

- [ ] Definir se é ROLETA (lead comprador) ou CAPTAÇÃO CORRETOR (recrutamento) — estrutura muda
- [ ] Nome da campanha segue `[TIPO][LOCAL][CÓDIGO/TIPO IMÓVEL][SISTEMA PORTAL]`
- [ ] ROLETA: criar 2 conjuntos (`[AB][POS MAN]` + `[INT][POS MAN]`), mesma geo/idade, um com interesses de imóveis, outro aberto
- [ ] Advantage+ Audience desativado em ambos
- [ ] Posicionamento manual: Feed + Story + Reels + Profile feed (FB), Feed + Story + Reels (IG) — nada de Marketplace/Audience Network/Messenger/WhatsApp
- [ ] Página certa pro tipo de campanha (lead comprador ≠ recrutamento corretor)
- [ ] Nome do anúncio: `[FORMATO][SUBTIPO] LOCAL`
- [ ] CTA: `APPLY_NOW` pra lead nativo, `WHATSAPP_MESSAGE` pra conversa
- [ ] Copy: gancho de dor → benefícios em lista → CTA direto
- [ ] Orçamento inicial de referência: R$13-14/dia por conjunto

---

## Pontos em aberto (confirmar com o usuário)

1. Terceiro conjunto "interesse + relacionamento" mencionado — não encontrado nas campanhas ativas. Existe em outra conta/cliente, ou é padrão a introduzir aqui?
2. Posicionamento automático em CAPTAÇÃO CORRETOR — intencional ou esquecimento?
3. Interesses de imóveis acima cobrem "primeiro imóvel" — há outro conjunto de interesses pra público de troca/upgrade de imóvel (não primeira compra)?
