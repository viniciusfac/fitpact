# 🏆 FitPact
PWA de planeamento de atividades físicas e acompanhamento entre amigos, com autenticação Supabase e partilha WhatsApp.

## Instalação
1. Execute `migration_v1_5.sql` no SQL Editor do Supabase **antes** de publicar esta versão.
2. Publique `index.html`, `app.js`, `manifest.webmanifest`, `icon.svg`, `icon-192.png` e `icon-512.png` na raiz do repositório GitHub Pages.
3. Confirme que a URL do projeto e a chave publishable em `app.js` correspondem ao seu Supabase.
4. Configure a Site URL e a Redirect URL para `https://viniciusfac.github.io/fitpact/`.

## Release notes
### v1.5.0 — 12/10/2026
**Added**
- Horários opcionais de início e fim, observação e marcador PT por treino.
- Seleção de atividade por lista suspensa, incluindo substituição.
- Edição de treino planeado.

**Changed**
- Meta semanal calculada automaticamente a partir dos dias com atividades planeadas que contam como treino.
- Conclusão de exercício com um toque, sem perguntar data.
- PT é um atributo do treino e não um exercício separado.
- Preservação do nome de apresentação ao iniciar sessão.

**Fixed**
- Impede que o login regrave o nome de apresentação existente.
- Redirecionamento de confirmação de email para o caminho `/fitpact/`.

### v1.4.3
- Correção de validação da URL do Supabase.
### v1.4.2
- Ícone no separador, versão no cabeçalho e estado de carregamento.
### v1.4.1
- Correção de carregamento da biblioteca Supabase.
### v1.4.0
- Autenticação, dados remotos, amizades e histórico no Supabase.

## Limitações conhecidas
- A sincronização é por consulta periódica; não há fila de alterações offline.
- A confirmação de uma atividade usa a data do dia planeado; reprogramação permanece como fluxo separado.
- As metas antigas na tabela `weekly_goals` não são usadas pela interface 1.5.
- Registos antigos de «Treino com PT» continuam como atividades até serem editados ou removidos manualmente.
- A validação em dois dispositivos e das políticas RLS ainda é necessária antes de partilhar com terceiros.

## Roadmap
- Sincronização em tempo real, modo offline com resolução de conflitos e relatórios históricos mais detalhados.
