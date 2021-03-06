# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Criação de página de boas vindas com termos de utilização de vpn](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/16) | :heavy_check_mark: |
[Salvar conteúdo das telas ao trocar de tela (verificar permitir alternar entre contas)](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/17) | :heavy_check_mark: |
[Documentar como habilitar funcionalidade no google class room](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/18) | :heavy_check_mark: |
[Adicionar funcionalidade de tirar foto](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/8) | :x: |
[Ferramenta de busca no FAQ](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/19) | :x: |

## Criação de página de boas vindas com termos de utilização de vpn

Foi criada uma tela ao abrir o app pela primeira vez solicitando que o usuário aceite os termos. É mostrado os termos presentes aqui: https://escolaemcasa.se.df.gov.br/index.php/politica-de-privacidade/ através de um webview.

![terms](./../../img/sprint4/terms.png)<br>

O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/64).

## Salvar conteúdo das telas ao trocar de tela (verificar permitir alternar entre contas

Foi adicionada uma linha ao manifest para que fosse possível salvar temporariamente o conteúdo da webview. Como era utilizado um único webview para duas páginas (google class, wikipedia) foi necessário adicionar uma webview pra cada uma das telas. Dessa forma o conteúdo do webview não é perdido ao trocar de tela.

O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/62).

## Documentar como habilitar funcionalidade no google class room

Atualmente na aplicação, o Google Classroom roda através de uma webview. A Webview é um navegador embutido na aplicação que pode mostrar páginas da internet.
Para habilitar novas funcionalidades que são dependentes de URLs externas, é necessário adicionar o domínio a uma lista de URLs permitidas. O trecho de código a seguir foi retirado do arquivo WebviewActivity.java, onde está localizado a lista de domínios permitidos.

```java
public boolean shouldOverrideUrlLoading(WebView webView, String urlParameter) {

if (url.startsWith("http") || url.startsWith("https")) {
   if (MyApplication.sdState == SdState.SD_AVAILABLE) {

       List<String> urlsPermitidas = new ArrayList<String>(30);

       urlsPermitidas.add("docs.google.com");

```
Ao adicionar o domínio “docs.google.com", será possível responder questionários via Google Forms direto do aplicativo, utilizando os dados patrocinados.

URLs que não estão na lista, serão abertas no navegador padrão do celular, saindo do escopo que abrange os dados patrocinados.

### Google Workspace API

Outra forma de utilizar o Classroom é através da API. Essa API fornece uma interface RESTful para gerenciar funcionalidades do Google Classroom.

#### Pré-requisitos

* Uma conta Google
* Android Studio SDK 1.2+
* Android SDK packages para API 23+, que incluem as últimas versões do Google Repository, Android Support Library e Google Play Services.

#### Preparando o Projeto

Dentro do arquivo build.gradle presente dentro do projeto Android, adicionar a seguinte dependência: 

```java
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:25.0.1'
    compile 'com.google.android.gms:play-services-auth:15.0.1'
    compile 'pub.devrel:easypermissions:0.3.0'
    compile('com.google.api-client:google-api-client-android:1.23.0') {
        exclude group: 'org.apache.httpcomponents'
    }
 compile('com.google.apis:google-api-services-classroom:v1-rev386-1.25.0') {
        exclude group: 'org.apache.httpcomponents'
    }
}
```

Com essa dependência no projeto, será possível usar várias funcionalidades. O exemplo simplificado a seguir mostra um trecho de código que mostra página inicial onde são listados as turmas que um aluno está matriculado.

```java
List<Course> courses = response.getCourses();
        if (courses == null || courses.size() == 0) {
            System.out.println("Turmas não encontradas");
        } else {
            System.out.println("Turmas:");
                courses.forEach(course -> System.out.printf("%s\n", course.getName()));
            }
        }
```

A documentação completa da API pode ser encontrada [aqui](https://developers.google.com/resources/api-libraries/documentation/classroom/v1/java/latest/overview-summary.html).

## Adicionar funcionalidade de tirar foto

A issue não foi desenvolvida nessa sprint. 

## Ferramenta de busca no FAQ

Foi criado um novo menu para ser inserido no layout, representando a SearchView. Para conectar o menu ao adapter da RecyclerView que existe na página de FAQ (contendo as dúvidas e respostas) foi necessário implementar a classe Filter dentro dele, onde o que é digitado é captado através dos listeners da SearchView e assim comparados com as dúvidas já existentes na RecyclerView. 

A implementação ainda não foi finalizada pois os listeners por algum motivo não estão funcionando, nem chegando a instanciar o menu na página de QuestionsActivity, mesmo que a implementação esteja igual a vários exemplos que verificamos nos estudos. 

![searchbox](https://user-images.githubusercontent.com/18038966/114096216-ce615880-9894-11eb-8963-1b4809e11d84.png)


## Referências Bibliográficas

**Google Classroom API.** Disponível em: https://developers.google.com/classroom/guides/get-started. Acesso em: 07 de abril de 2021.

## Histórico de Revisão

Data | Versão | Descrição | Autor |
:---:|:------:|-----------|-------|
08/04|0.1 | Criação da Página | [Rafael Ribeiro](https://github.com/rafaelflarrn) |
08/04|1.0 | Adicionando review | [Pedro Igor](https://github.com/pedroeagle) |
08/04|1.1 | Adicionando texto sobre Ferramenta de busca no FAQ | [Lucas Gomes](https://github.com/LGomees) |
