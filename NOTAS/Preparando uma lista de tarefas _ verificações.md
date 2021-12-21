## 1.  Auditoria / verificação / inventário / revisão:

- Definição de escopo: Você é responsável pela eletricidade, laptops, desktops, suporte de software, telefones celulares, servidor, serviços online que a empresa utiliza, definição de políticas, etc.

- Documentação geral: não melhore até que você entenda o ambiente (faça backup antes de mudar)

- Inventário de serviços essenciais: identifique os serviços essenciais e onde eles estão hospedados; identifique quem é responsável por eles, se não for você

- [DR] Plano de recuperação de desastres: os backups estão funcionando corretamente? Rotação de backup? Último teste de DR? Automatizado? Em caso de minha ausência?

- [BC] Plano de Continuidade de Negócios

- [BIA] Análise de impacto nos negócios

- Topologia de rede: configuração (backup?), Senhas, roteadores, gateways, sub-redes, vlans, endereços estáticos, dhcp, cabos rotulados

- Fonte de alimentação / UPS

- ISP: contato, acordos, SLA, contratos, números de circuito

- Suporte aos componentes do ambiente: contato, convênios, consultores, SLA, contratos; renovar / corrigir quaisquer problemas relativos à falta de suporte, obter peças de reposição em tempo hábil, situação de contrato de manutenção

- VPN / acesso remoto

- Políticas de firewall: entenda o que está sendo permitido / bloqueado

- AV: existente em sistemas (servidores, desktops, celulares), ativado, atualizado, exclusões personalizadas

- Repositório de senha: existente? Atualizado?

- Contas de administrador: serviços em execução

- Data de validade dos certificados de criptografia

- Atualizações do Windows: políticas, funcionando?

- Atualizações de aplicativos: políticas? automatizado?

- Inventário de software: licenças (com encargos), garantia, legal
 
- Estoque de hardware: garantia, peças de reposição, situação de fim de ciclo de vida
 
- Tarefas do agendador em servidores
 
- Revisão de GPOs

- Revisão de scripts. Onde eles estão armazenados?

- Observar rede / sistemas: para saber qual é o comportamento "normal"; problemas conhecidos; verificar logs

- Estudo dos relatórios das últimas auditorias

- Análise de processos para incidentes, gerenciamento de problemas, solicitações de serviço, escalonamento [ITIL]

- [Opcional]: Políticas de gerenciamento de documentos

- [Opcional]: Sistemas telefônicos - VOIP; Skype for Business; outras soluções / canais de comunicação

## 2. Preparar / fazer

- Kit de crise: local seguro contra incêndio, contatos do fornecedor, números de emergência, chave de fenda, toalha, desodorante, carregador de telefone, medicamento para dor de cabeça, testador de cabo, menu para viagem

- Reuniões: com chefes de departamentos, o que sua equipe faz, o que eles usam, quais são seus principais problemas

- Faça uma "pequena vitória": lista que você pode corrigir e que lhe dará um pouco de cara para trabalhar - isso contribuirá para que as pessoas confiem que você é um profissional para prestar um serviço.

## 3. Mudanças

- Orçamento: agora e no futuro; limitar PCs / laptops extras inúteis

- Categorizar tíquetes: para análise futura

- Software de monitoramento: Icinga (ou outro software); iLo / iDrac enviando e-mails; habilitar monitoramento inteligente em discos, UPSes

- Limpe as permissões preguiçosas

- IDS / IPS (Sistema de detecção de intrusão / Sistema de prevenção de intrusão) se não houver

- Tenha um armazenamento de itens de hardware de baixo custo (mouses, teclados, etc)