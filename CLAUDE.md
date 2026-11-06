# Regras fixas — Meta Ads

Regras padrão pra qualquer campanha/conjunto de anúncios criado ou editado nessa conta. Valem sempre, exceto se o usuário pedir explicitamente o contrário numa campanha específica (é sempre excepcional, não o padrão).

- **Advantage+ Audience: sempre desativado.** `targeting_automation.advantage_audience = 0`, com `advantage_audience_off_reason = ADVERTISER_REQUESTED_OFF`. Direcionamento (interesses, idade, etc.) é filtro real, não sugestão pra IA da Meta.
- **Posicionamentos: sempre manual, nunca Advantage+ Placements.** Excluir posicionamentos desqualificados por padrão — ex: WhatsApp (quando a campanha não for de Click-to-WhatsApp), Audience Network, e vídeo fora de Facebook/Instagram. Manter só os posicionamentos que fazem sentido pro objetivo (normalmente Feed + Reels de Facebook e Instagram).
