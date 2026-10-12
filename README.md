# FitPact 1.7.1 — Atualização corretiva

## Instalação
1. Faça backup do projeto Supabase antes de qualquer migração.
2. Com a migração v1.7.0 já aplicada, execute `migration_v1_7_1.sql` no SQL Editor do Supabase.
3. Publique `index.html`, `app.js`, `manifest.webmanifest` e os ícones no GitHub Pages.
4. Feche e reabra a PWA instalada (se necessário, reinstale para atualizar o nome exibido).
5. Valide com duas contas reais, especialmente recuperação de senha, remoção bilateral, reativação e políticas RLS.

## Novidades
- FP-14/15: fluxo de recuperação com listener registrado antes da sessão; notificação de solicitação já presente.
- FP-16: troféus e medalhas mantidos, aguardando teste real.
- FP-17: converter recuperação em treino extra sem elevar a meta (campo `extra_workout`).
- FP-18: versão 1.7.1 no título, HTML e manifesto.
- FP-19: nomes dos amigos na gestão, evitando IDs na interface.
- FP-20/21/27: histórico unificado de reações, incentivos, respostas, com data/hora.
- FP-22: código de convite preservado no primeiro acesso usando sessionStorage.
- FP-23: filtro por amigo no feed e nas interações.
- FP-24: gestão de convites e amizades em Configurações.
- FP-25: permitir/silenciar incentivos individualmente, aplicado no banco.
- FP-26: remoção bilateral lógica, aviso ao removido e reativação mediante nova aceitação.

## Observações
- Interações antigas com resposta anterior à migração não possuem data exata da resposta; usa-se a data original como fallback.
- As notificações são internas, não são push.
- A migração depende da estrutura e das funções da versão 1.7.0; valide no Supabase antes de disponibilizar a terceiros.

---

# FitPact 1.7.0 — FitPact Social

## Release Notes (12/10/2026)
- Nova aba **Amigos**: feed com os últimos treinos concluídos dos amigos aceitos e conquistas da meta semanal.
- Reações 👏 🔥 💪 🏆 para treinos concluídos e semanas com meta atingida. Cada usuário pode atualizar sua reação.
- Incentivos 💪, 🤝, 👀 e 🏃, com limite de um por amigo a cada 24 horas (também aplicado no Supabase).
- Caixa de incentivos recebidos, respostas rápidas e marcação de leitura; reações recebidas também são apresentadas.
- Em Configurações, opção para desativar o recebimento de incentivos.
- O banco só autoriza interações entre amizades aceitas; as tabelas têm RLS.

## Instalação — atenção à ordem
1. Faça backup do projeto Supabase e execute **migration_v1_7_0.sql** no **SQL Editor**. Este passo é obrigatório e deve ocorrer **antes** de publicar a aplicação.
2. Envie os arquivos de aplicação deste ZIP para a raiz do repositório GitHub Pages.
3. Atualize a página e entre na aba **Amigos**.
4. Teste com duas contas já vinculadas por amizade aceita.

## Problemas conhecidos / limites
- As notificações são exibidas dentro da aplicação; **não** há notificações push nem e-mails de incentivo.
- A sincronização utiliza a atualização periódica existente (~30 segundos), não tempo real por websocket.
- A interface mostra até cinco treinos recentes por amigo e limita o histórico de interações carregado; não há paginação.
- Não há chat livre; apenas quatro respostas rápidas.
- A limitação de incentivo é por remetente e destinatário, não por tipo de mensagem.
- O banco deve estar com a migração v1.5.0 já aplicada.

---

# FitPact 1.6.4 — Release Notes

## Melhorias no compartilhamento
- Copiar resumo e Compartilhar pelo WhatsApp utilizam a mesma função e o mesmo formato.
- Dias mostram apenas emojis de atividades, indicador de PT 👤 e status.
- Histórico aparece imediatamente abaixo de Dias concluídos, antes da lista de dias.
- Dias concluídos: um 🏆 por dia até a meta e uma 🥇 por dia adicional acima da meta. Sem dias concluídos, mostra —.
- Legenda dinâmica ao final, com cada atividade da semana uma única vez; 👤 explicado apenas quando utilizado.
- Datas do resumo em formato brasileiro.
- Nenhuma alteração no banco de dados.

## Problemas conhecidos
- Treinos concluídos em data diferente da planejada aparecem na linha do dia planejado no resumo; contagem de dias concluídos considera a data efetiva.
- O resumo pode ficar longo em semanas com muitas atividades e um histórico extenso.
- Consulte também os problemas conhecidos das versões anteriores abaixo.

---

# FitPact 1.6.2 — Release Notes

## Correções
- Configurações exclusivamente pessoais: removido o seletor «Ver: Eu»; amigos apenas no Histórico.
- Plano Semanal, biblioteca e compartilhamento usam sempre a conta autenticada, independentemente do amigo selecionado no Histórico.
- Conclusão de exercícios substituídos preserva a atividade efetivamente realizada, inclusive em nova conclusão.
- Reprogramação de atividade substituída preserva a substituição e os atributos PT, horário e observações.
- Filtros de Histórico usam a data da atividade (data de conclusão para concluídas, data planejada para as demais), sem depender da data de criação. Intervalos de meses tratados com calendário local.
- Repetir semana anterior bloqueado em semanas passadas, inclusive com verificação no momento do clique.

## Instalação
Substitua os arquivos do repositório GitHub Pages pelos deste ZIP. Não há nova migração SQL, desde que a migração da v1.5.0 já tenha sido aplicada.

## Problemas conhecidos / validação pendente
- Ainda é necessário validar as correções com dados reais no Supabase, especialmente os filtros por período e as substituições.
- Em semanas parcialmente abrangidas pelo filtro, o indicador de meta semanal reflete a semana inteira, enquanto os totais de atividades e dias refletem apenas o intervalo filtrado.
- A repetição de semanas pode gerar registros duplicados se executada várias vezes; verificar antes de repetir.
- Não há service worker para uso totalmente offline.

# FitPact

PWA para planejamento semanal de exercícios, acompanhamento entre amigos e compartilhamento pelo WhatsApp.

## Instalação

Publique `index.html`, `app.js`, `manifest.webmanifest` e os ícones na raiz do GitHub Pages. Configure a URL do site e de redirecionamento no Supabase Authentication. A versão 1.6.0 utiliza a estrutura de banco já migrada para a 1.5.0.

## Release Notes

### v1.6.1 — 12/10/2026
- **Fixed:** preservação da atividade efetivamente realizada ao confirmar novamente uma substituição; reprogramação conserva PT, horários e observações.
- **Fixed:** filtros do histórico por datas da atividade (`scheduled_date`/`completed_date`), com intervalos de calendário; ordenação decrescente por semana.
- **Fixed:** recuperação e treino mutuamente exclusivos no mesmo dia, tanto na inclusão quanto na reprogramação.
- **Changed:** ícone 🕘 para consultar a atividade substituída, separado do botão 🔄 de substituir.
- **Added:** aba Configurações; seletor de histórico de amigos; Reiniciar semana com confirmação e bloqueio para semanas anteriores.
- **Changed:** ordem dos indicadores: Meta de dias, Atividades concluídas, Dias concluídos, Resultado.
- **No database migration required** após v1.5.0.


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
- Filtros por períodos parciais agrupam atividades por semana; a meta exibida é a meta da semana completa.
- Reiniciar semana apaga permanentemente os registros com data planejada naquela semana, inclusive os resultados; registros originados em outras semanas não são excluídos.
- O histórico de amigos depende das políticas RLS de leitura entre amizades aceitas.
- O acesso entre amigos e as políticas RLS precisam de teste em duas contas antes de utilização real.

## Roadmap
- Sincronização offline e notificações de mudanças entre amigos.
- Melhoria de reagendamento com seletor visual de datas.


## Release Notes — v1.6.4 (12/10/2026)

- Incluído **Esqueci minha senha** na tela de entrada, enviando link de recuperação via Supabase Auth.
- Adicionada tela de redefinição de senha com confirmação e validação básica.
- Em Copiar resumo / WhatsApp, o histórico não inclui a semana selecionada e apresenta as semanas anteriores da mais antiga para a mais recente.
- Removidas ampulhetas dos exercícios ainda não concluídos no resumo compartilhado.
- Dias concluídos igual a zero mostra `0`; valores positivos seguem a regra de 🏆 até a meta e 🥇 acima da meta.

### Configuração necessária para recuperação de senha

No Supabase Authentication → URL Configuration, verifique que `https://viniciusfac.github.io/fitpact/` consta como Site URL ou Redirect URL permitido. O e-mail de recuperação depende da entrega de e-mails pelo Supabase (e de limites de envio do projeto).

### Limitações conhecidas

- Recuperação de senha requer internet e acesso ao e-mail cadastrado.
- Fluxo de recuperação e e-mail ainda precisam de teste ponta a ponta no ambiente publicado.
- Histórico compartilhado considera as últimas 25 semanas com registros anteriores à semana selecionada.

## Release Notes — v1.6.5 (12/10/2026)
- A seleção para substituir uma atividade não apresenta a atividade atual (nem outra atividade com o mesmo nome).
- Recuperação não apresenta ampulheta no Plano Semanal.
- Em Configurações, é possível compartilhar ou copiar um convite com apresentação do FitPact, link da aplicação e código de amizade.
- Links `?amigo=UUID` preenchem o campo de convite; o usuário precisa confirmar o envio, sem associação automática.
- A biblioteca impede excluir atividades já associadas a treinos (inclusive registros históricos) e impede criar nomes duplicados, ignorando diferenças de maiúsculas e espaços.
- Não é necessária migração SQL para atualizar da v1.6.4.

### Problemas conhecidos / observações
- O compartilhamento nativo depende de suporte do navegador e de contexto HTTPS; há opção de copiar e fallback para WhatsApp.
- A proteção contra nomes duplicados é feita na aplicação. Para garantir unicidade mesmo em gravações simultâneas feitas por dispositivos diferentes, é recomendável uma restrição adicional no banco de dados.
- A validação com múltiplos usuários e navegadores ainda deve ser realizada.


Migração 1.7.0 corrigida: idempotência das políticas; se a execução anterior falhou, execute migration_v1_7_0.sql corrigida e depois migration_v1_7_1.sql.
