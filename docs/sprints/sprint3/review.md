# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Enviar o consumo de dados patrocinados para o elasticsearch](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/15) | :x: |
[Criar um método para enviar requisição a cada segundo](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/14)| :heavy_check_mark: |
[Adicionar barra de controle de histórico](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/70)| :heavy_check_mark: |
[Verificar mais formas de abrir docs](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/67) | :heavy_check_mark: |
[Verificar mais formas de inserir formulário](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/50) | :heavy_check_mark: |
[Documentar o processo para a habilitação de funcionalidades do google classroom](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/53) | :x: |

## Enviar o consumo de dados patrocinados para o elasticsearch


## Criar um método para enviar requisição a cada segundo

Essa issue já foi desenvolvida anteriormente, onde o PR ainda não foi revisado. Também está dependendo da aprovação do PR que conserta o Travis. 

## Adicionar barra de controle de histórico

Ao utilizar o webview do app em alguns momentos o app não responde mais aos toques dentro do navegador e ao pressionar o botão de voltar nada acontece ou o app simplesmente fecha. Para solucionar isso é necessário clicar em outro item na barra de navegação e então retornar a página que estava sendo utilizada. Como solução foi adicionado um botão auxiliar flutuante que permite que o usuário volte até a página anterior sem muitos problemas além de não fechar o app ao realizar tal ação.<br>
![back_button](../../img/sprint3/back_button.png)<br>

O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/60).

## Verificar mais formas de abrir docs
Existem algumas formas que permitem abrir docs no app:<br>
    - Link completo do documento no formato `https://docs.google.com/document/d/${ID_DO_DOC}`. <br>
    - Links no formato `https://drive.google.com/file/d/${ID_DO_DOC}`. Porém o arquivo é aberto apenas para leitura e é necessário aplicar zoom para ler determinados conteúdos. <br>
    - Docs embutidos, isto é, sem link. O documento abre porém pode tomar algum tempo. O motivo dessa issue ter sido aberta: durante alguns testes o documento não abriu, porém durante a issue o documento abriu tomando certo tempo. <br>

O essencial é que qualquer documento embutido abra sem problemas. Porém a conta que temos acesso para testes não nos permite inserção de novos conteúdos<br>

A documentação foi realizada por meio de comentário na issue do repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/67). 

## Verificar mais formas de inserir formulário

Links encurtados para formulários são redirecionados para uma página que não funciona, é apresentada a seguinte tela:<br>
![page_not_available](./../../img/sprint3/page_not_available.png)<br>
Alguns outros links até abrem porém em um app externo, instalado no dispositivo, e não deveria ser o comportamento do app.

A solução encontrada para o problema apresentado foi realizar uma interceptação entre todos os links que são clicáveis dentro do aplicativo. Para tal, utilizamos uma regex para links encurtados e consultamos a URL do rollback que estava dentro do header 'location' no elemento S.browser_fallback_url.

Realizando essa alteração foi possível abrir o formulário com link encurtado normalmente:<br>
![short_link_forms](./../../img/sprint3/short_link_forms.png)<br>

Sendo assim, foram mapeadas as seguintes formas de inserir formulários:<br>
    - Link completo do formulário no formato `https://docs.google.com/forms/d/${ID_DO_FORMULARIO}`<br>
    - Link encurtado no formato `https://forms.gle/${ID_ENCURTADO_DO_FORMULARIO}`. Corrigido nessa issue, o PR foi aberto no repositório oficial e pode ser encontrado [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/59).<br><br>
Obs: Links no formato `https://drive.google.com/file/d/${ID_DO_FORMULARIO}` podem ser abertos porém o estudante não conseguirá responder ao questionário, este será apenas mostrado sem interação para respondê-lo.<br>

É necessário analisar se formulários inseridos sem link (como arquivo) no app funcionam como deveria. Porém a conta que temos acesso para testes não nos permite inserção de novos conteúdos.<br>

## Documentar o processo para a habilitação de funcionalidades do google classroom

A issue não foi desenvolvida por conta de um dos riscos analisados anteriormente terem se concretizado. Um dos membros desistiu da matéria por problemas pessoais, deixando a issue como dívida técnica. 

## Histórico de Revisão

Data | Versão | Descrição | Autor |
:---:|:------:|-----------|-------|
22/03|0.1 | Criação da Página | [Geise Saunier](https://github.com/GeiseSaunier) |
22/03|0.2 | Verificar mais formas de inserir formulário | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
22/03|0.3 | Verificar mais formas de abrir docs | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
24/03|1.0 | Atualiza issue de mais formas de inserir formulário | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
24/03|1.1 | Adiciona issue de botão de navegação no histórico | [Pedro Igor](https://github.com/pedroeagle) |
24/03|1.2 | Adiciona issue de formas de abrir docs | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
24/03|1.3 | Adiciona issue de criar método para enviar requisição a cada segundo e Consertando checkbox de tarefas | [Lucas Gomes](https://github.com/LGomees)|
15/05|1.4 | Adiciona link para comentário da documentação | [Pedro Igor](https://github.com/pedroeagle) |
