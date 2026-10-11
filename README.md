# FitPact 1.4 — Supabase

PWA com login por email, biblioteca de atividades por utilizador, planeamento, substituições, reprogramação, metas por dias distintos, histórico completo, convite privado por código UUID e partilha WhatsApp.

## Publicação
1. Publicar esta pasta em HTTPS (por exemplo, GitHub Pages).
2. No Supabase: Authentication > URL Configuration, configurar Site URL e Redirect URLs com a URL HTTPS da aplicação (necessário para confirmação por email).
3. Em Authentication > Providers > Email, manter a confirmação por email ativa.
4. Executar primeiro o ficheiro `fitpact_schema_v1.sql` no SQL Editor (já feito no projeto). Não executar novamente.
5. Registar duas contas, confirmar emails, trocar códigos UUID e aceitar convite.

## Limitações importantes
- A sincronização usa leituras do Supabase ao entrar, voltar à aplicação e a cada 30 segundos enquanto aberta; não é realtime push.
- Requer Internet para ler/gravar. Não há fila de escrita offline; não prometer funcionamento offline nesta versão.
- Não migra automaticamente o armazenamento local da v1.3. Fazer backup antes de substituir a aplicação.
- A chave publishable é pública e deve ser protegida pelas políticas RLS da base de dados.
- A biblioteca supabase-js é carregada por CDN; é necessária Internet na primeira carga.
- A instalação PWA requer publicação em HTTPS e configuração de service worker numa futura revisão.

## Correção 1.4.1
Corrige o endereço do script UMD supabase-js (antes usava supabase.min.js, não disponível na distribuição), adiciona fallback unpkg e mensagens de erro mais claras. Substituir index.html e app.js na raiz do repositório.
