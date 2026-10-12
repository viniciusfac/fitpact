# FitPact 1.6.3 — Release Notes

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
