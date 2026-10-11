# FitPact

PWA para planejamento semanal de exercícios, acompanhamento entre amigos e compartilhamento pelo WhatsApp.

## Instalação

Publique `index.html`, `app.js`, `manifest.webmanifest` e os ícones na raiz do GitHub Pages. Configure a URL do site e de redirecionamento no Supabase Authentication. A versão 1.6.0 utiliza a estrutura de banco já migrada para a 1.5.0.

## Release Notes

### v1.6.0 — 12/10/2026
- **Added:** abas Plano Semanal, Histórico e Atividades; filtros do histórico; recuperação como opção do dia.
- **Changed:** interface em português brasileiro; notificações temporárias no topo; PT como atributo; substituições indicadas por ícone; resumo com “Concluído” e “Histórico”.
- **Fixed:** estatísticas filtradas pelo usuário selecionado; botão Atualizar removido.
- **Security:** permissões e políticas RLS devem continuar configuradas e testadas no Supabase.

### v1.5.0
- **Added:** horários opcionais, observações e indicador de personal trainer.
- **Changed:** meta calculada a partir dos dias com treinos planejados.

### v1.4.3
- **Fixed:** validação da URL do Supabase.

### v1.4.2
- **Added:** ícones e versão no cabeçalho.
- **Fixed:** feedback de inicialização.

### v1.4.1
- **Fixed:** carregamento da biblioteca Supabase.

### v1.4.0
- **Added:** autenticação, sincronização, amizades e histórico no Supabase.

## Limitações conhecidas
- Recuperações antigas registradas como atividade permanecem no histórico; podem exigir limpeza manual.
- A sincronização depende de conexão à Internet; não há fila offline.
- O histórico personalizado filtra pela semana inicial.
- O acesso entre amigos e as políticas RLS precisam de teste em duas contas antes de utilização real.

## Roadmap
- Sincronização offline e notificações de mudanças entre amigos.
- Melhoria de reagendamento com seletor visual de datas.
