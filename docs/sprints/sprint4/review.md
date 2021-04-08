# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Criação de página de boas vindas com termos de utilização de vpn](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/16) | :heavy_check_mark: |
[Salvar conteúdo das telas ao trocar de tela (verificar permitir alternar entre contas)](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/17) | :heavy_check_mark: |
[Documentar como habilitar funcionalidade no google class room](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/18) | :heavy_check_mark: |
[Adicionar funcionalidade de tirar foto](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/8) | :x: |
[Ferramenta de busca no FAQ](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/19) | :x: |

## Criação de página de boas vindas com termos de utilização de vpn

## Salvar conteúdo das telas ao trocar de tela (verificar permitir alternar entre contas

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

## Ferramenta de busca no FAQ

## Referências Bibliográficas

**Google Classroom API.** Disponível em: https://developers.google.com/classroom/guides/get-started. Acesso em: 07 de abril de 2021.

## Histórico de Revisão

Data | Versão | Descrição | Autor |
:---:|:------:|-----------|-------|
08/04|0.1 | Criação da Página | [Rafael Ribeiro](https://github.com/rafaelflarrn) |