# FitPact 1.4.2 — correção do estado de inicialização e ícones

## Atualização
Carrega **todos** os ficheiros desta pasta na raiz do repositório GitHub Pages `fitpact`, substituindo os anteriores. Não coloques a pasta inteira como subpasta.

## Alterações
- Ícone do separador (`icon.svg`) e ícones PNG para instalação da PWA.
- Versão visível no cabeçalho e título do separador.
- Mensagem de estado deixa de ficar em «A carregar...» após verificação bem-sucedida.
- Tempo limite e aviso caso a verificação de sessão demore mais de 10 segundos.
- Parâmetro de versão em `app.js` para evitar cache antiga.

## Teste
Aguarda o GitHub Pages publicar; abre em janela anónima ou faz Ctrl+Shift+R. Deverás ver «Pronto. Entra com a tua conta ou cria uma nova.» sem login. Caso apareça um erro, envia o texto exato.

**Nota:** ainda não testámos a ligação real ao projeto Supabase nem as permissões da base de dados a partir deste ambiente.
