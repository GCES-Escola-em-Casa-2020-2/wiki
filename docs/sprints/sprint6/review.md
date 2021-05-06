# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Implementação de testes](colocar_link) | |
[Implementar Solid](colocar_link) | |
[Pesquisar viabilidade de utilização do Google Classroom Api](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/18) |:heavy_check_mark: |

## Pesquisar viabilidade de utilização do Google Classroom Api
A pesquisa foi realizada com objetivo de, por meio da api, realizar a submissão de atividades no Google Classroom. A partir dessa viabilidade utilizar o Google Drive Api e realizar então a submissão de fotos (uma issue atualmente sem solução do projeto).

### Passo a passo para criação e submissão de atividade
É possível realizar a submissão de atividades via classroom api. Isso pode ser utilizado para solucionar o problema ao submeter fotos nas atividades.
Passo a passo de como isso deve ser feito:

**1** - Criar um projeto e uma autorização oauth respectiva aqui: console.cloud.google.com/apis/credentials

**2** - Realizar o download do arquivo de credenciais dessa autorização oauth. Se trata de um arquivo .json
com as seguinte informações (é necessário obter todas): client_id, project_id, auth_uri, token_uri, 
auth_provider_x509_cert_url, client_secret, redirect_uris (esse pode ser um endereço localhost qualquer, 
o código de autorização fica disponível na url possibilitando acesso direto sem a criação de uma página 
de callback)

**3** - Solicitar o token via oauth. O arquivo do passo anterior será utilizado na solicitação do token.json que pode ser solicitado seguindo
este guia: https://developers.google.com/classroom/guides/get-started. É possível realizar esta etapa em diversas
linguagens. É importante que sejam solicitadas todas os escopos dentro do classroom, isso é definido por meio 
do array: 
const SCOPES = ["https://www.googleapis.com/auth/classroom.courses", "https://www.googleapis.com/auth/classroom.coursework.me", 
"https://www.googleapis.com/auth/classroom.coursework.me.readonly", "https://www.googleapis.com/auth/classroom.coursework.students", 
"https://www.googleapis.com/auth/classroom.coursework.students.readonly"];

**4** - Utilizar a api. Após solicitado o token.json é possível realizar qualquer requisição disponível na documetação passando sempre o arquivo de token.
O guia auxilia bastante a forma como esse token deve ser utilizado além dos endpoints e bodies. O token tem um curto prazo de validade, logo uma dificuldade
pode ser gerar esse token constantemente.
Link do guia: https://developers.google.com/classroom/guides/get-started

Na própria api é possível realizar consultas do id de todos os cursos, atividades e submissões para que sejam realizados os passos abaixo.

**5** - Criar uma atividade. Para que uma atividade seja submetida via api esta precisa ser criada também via api.
Uma atividade pode ser criada da seguinte forma (exemplo em node): 
classroom.courses.courseWork.create({courseId: $idDaTurma, requestBody:{title: $tituloDaAtividade, workType: $tipoDeAtividade, state: 'PUBLISHED'}

**6** - Realizar uma submissão. Assim que uma atividade é criada é criada também uma submissão para cada estudante. Esta submissão fica vazia até
que o estudante entregue a atividade. É possível então modificar os anexos de uma atividade sendo possível enviar um arquivo do drive (resolvendo 
o problema de subsmissão de imagens), video do youtube, link e um formulário. O exemplo abaixo envia um link como submissão.
await classroom.courses.courseWork.studentSubmissions.modifyAttachments({courseId: $idDaTurma, courseWorkId: $idDaAtividade, id: $idDaSubmissao, 
requestBody:{addAttachments:[{link:{url: $url, title: $tituloDaUrl}}]}})