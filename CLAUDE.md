# Regras fixas — Meta Ads

Regras padrão pra qualquer campanha/conjunto de anúncios criado ou editado nessa conta. Valem sempre, exceto se o usuário pedir explicitamente o contrário numa campanha específica (é sempre excepcional, não o padrão).

- **Advantage+ Audience: sempre desativado.** `targeting_automation.advantage_audience = 0`, com `advantage_audience_off_reason = ADVERTISER_REQUESTED_OFF`. Direcionamento (interesses, idade, etc.) é filtro real, não sugestão pra IA da Meta.
- **Posicionamentos: sempre manual, nunca Advantage+ Placements.** Excluir posicionamentos desqualificados por padrão — ex: WhatsApp como superfície de exibição (`whatsapp_positions`), Audience Network, e vídeo fora de Facebook/Instagram. Isso é independente do `destination_type` da campanha: mesmo numa campanha de Click-to-WhatsApp (clique abre conversa no WhatsApp), o anúncio continua sendo exibido só no Feed/Reels de Facebook e Instagram — nunca dentro do próprio app do WhatsApp, salvo exceção explícita do usuário.
- **Página: sempre a certa pra cada conta/cliente.** Nunca usar página de um cliente em campanha de outro. Confirmar qual página pertence à conta antes de criar o criativo.
- **Criativo: sempre reaproveitar vídeo já existente na conta, 1 vídeo só por anúncio.** Buscar entre os vídeos já upados (`ads_get_ad_videos`) e escolher o que fizer sentido pro público/oferta. Só sair desse padrão (mais de 1 vídeo, vídeo novo, imagem) se o usuário pedir algo personalizado — isso é sempre exceção, não o padrão.
- **Otimização: sempre maximizar volume de leads por padrão** (ex: `optimization_goal: LEAD_GENERATION`, bid autobid/highest volume). Só usar lead qualificado (`QUALITY_LEAD`) ou outra otimização quando o usuário pedir explicitamente — é sempre exceção, não o padrão.
