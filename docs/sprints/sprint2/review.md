# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Filtrar acesso a internet antes de abrir o WebView](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/5) | :heavy_check_mark: |
[Documentar todo o processo de publicação do app na Google Play e Apple Store](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/6)| :heavy_check_mark: |
[Melhorar FAQ](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/3)| :heavy_check_mark: |
[Documentar o processo de atualização do SDK datami](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/52) | :heavy_check_mark: |
[Abrir formularios do google](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/50) | :heavy_check_mark: |
[Documentar o processo para a habilitação de funcionalidades do google classroom](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/53) | :x: |
[Adicionar funcionalidade de tirar foto](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/49) | :x: |

# Tarefas

## Filtrar acesso a internet antes de abrir o WebView

Foi criada uma tela informando que o usuário está sem acesso a internet. Além disso foi adicionado um botão para que o usuário tente se conectar novamente. O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/55).

## Documentar todo o processo de publicação do app na Google Play e Apple Store

A publicação de aplicativos nas lojas disponíveis (Play Store e App Store), em geral, não é tarefa trivial, ambas possuem princípios rígidos para manter esse ecossistema seguro para seus usuários e sempre oferecer aplicativos de alta qualidade. O Escola em Casa, por sua vez, possui uma complexidade a mais devido aos fatores envolvidos na publicação, principalmente a empresa datami e a VPN utilizada. 

A **empresa datami** é uma empresa que possui contrato com o Governo do Distrito Federal - GDF, ela é quem faz a interface entre as operadoras de celular com o aplicativo, fazendo com que este funcione sem que o usuário tenha planos de dados ativos. 

A **VPN** pessoal utilizada nesta aplicação atende a alguns propósitos principais:
1) Oferecer uma navegação segura ao usuário;
2) Contar o uso de dados em bytes;
3) Prevenir o uso indevido e interceptação da conexão para proteger os interesses da entidade patrocinadora;
4) Oferecer, também, uma navegação segura para estudantes, para que assim o governo ofereça acesso a educação gratuita.

O processo de publicação segue os seguintes protocolos:

- Criar a build do aplicativo, isto é, abrir o android studio, clicar em build, em seguida pressionar a opção correspondente a make project. Se tudo estiver funcionando corretamente, clicar em build novamente. Ao seguir essas etapas, a buil do aplicativo é criada.
- Submeter a build, o datami precisa ser validado. Além disso, é necessário habilitar a opção de wifi;
- Com o wifi habilitado, submeter para testflight;
- Entrar com o processo de publicação, explicando a forma de uso da VPN, pois embora a conexão VPN habilite uma conexão segura, nenhum dado pessoal é coletado do usuário e não há nenhuma interferência com outros tráfegos de dados do aparelho. Todo o tráfego de dados do usuário é respeitado e permitido e nenhum dado é coletado ou armazenado. Além disso, uma mensagem clara é apresentada ao usuário informando-lhe da VPN.
- As lojas vão necessariamente recusar a publicação por causa da VPN, devido a insegurança no uso dessas APIS para importar bibliotecas não recomendadas;
- Em seguida, deve-se entrar em contato com o suporte das lojas para explicar que a aplicação utiliza dados patrocinados, ou seja, o aplicativo coleta apenas dados anônimos, no intuito de aferir a quantidade de dados trafegados de forma global e por operadora envolvida no processo, para confecção de fatura relativo aos dados trafegados, por se tratar de dados patrocinados pelo Governo do Distrito federal junto as operadoras de telefonia móvel integrantes do chamamento público. 
- A última etapa do processo é de fato submeter a aplicação para revisão e publicação na Play Store. É necessário criar uma conta no [Google Play Console](https://play.google.com/console/signup) preenchendo todas as informações do desenvolvedor. 

Após criada a conta, basta clicar em "Criar app" na primeira página. Será necessário preencher vários metadados do app tais como faixa etária do público alvo, restrições de idade, categoria do conteúdo, contas para que a equipe da Google possa testar, configurações de anúncios, submissão de certificado de privacidade dentre outros. 

Algumas configurações a serem especificadas são mostradas como pendentes ao clicar na opção "Produção" ou "Teste" a depender do tipo de submissão que será realizado, na barra lateral. Nessa mesma página é possível selecionar o APK (arquivo executável do aplicativo, em formato .apk) ou um arquivo em formato .aab (Android App Bundles). Também é possível especificar a versão do app além de diversas descrições que aparecerão na página do aplicativo. É obrigatória a submissão de um banner e alguns prints da aplicação em funcionamento. É, inclusive, recomendado que o nome desses arquivos de imagem sejam significativos para que sejam sugeridos em pesquisas do Google, aumentando assim o alcance do app. Após toda essa etapa de detalhamento do aplicativo basta clicar em "Iniciar lançamento para Produção". 

A issue foi criada no repositório oficial e adicionado um comentário com todo o processo de publicação e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/issues/66).

## Melhorar FAQ
Os comentários sobre o aplicativo foram analisados e posteriormente criamos mais algumas dúvidas na página de 'Dúvidas Frequentes'. Além disso, foi criada uma RecyclerView para remodelar o formato de como as dúvidas e respostas eram mostradas na tela. Com a implementação dessa view, os usuários podem visualizar todas as dúvidas cadastradas, e podem clicar em cima de cada uma para visualizar sua respectiva resposta. O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/56).

## Documentar o processo de atualização do SDK Datami
Para atualizar o SDK do Datami é necessário baixar o SDK mais atual no [Site do Datami](https://developer.datami.com/#/onboardhome/sdkintegrationkit). É necessária uma conta que pode ser criada gratuitamente. Basta selecionar "android" em seguida a versão mais atual e então baixar o arquivo "vpnsdk-android.zip", após extraído será encontrado um arquivo em formato ".aar". O arquivo deve ser adicionado ao diretório "app/libs" no diretório raiz. Dele virão todos os métodos necessários para a utilização do Datami. Para cada atualização do SDK é necessário realizar o download e adiçaõ do arquivo ao projeto. O PR foi aberto para o repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/57).

## Abrir formularios do google

Essa funcionalidade já está habilitada no app. Ao estudar o código, foi encontrada a implementação dessa funcionalidade através do WebView. Tanto o link normal quanto o link curto estão nas lista de URLs permitidas.
<p align="justify">Para testar a funcionalidade, foram encontradas algumas dificuldades por não possuirmos uma conta com mais permissões. Assim, para contornar essa limitação, foi acessada a conta do Google Drive pelo computador. Foi criado um formulário e colocados os links(normal e curto) deste formulário em um documento dentro do Drive. No aplicativo, acessei o Google Drive, acessei os documentos com os links, ambos funcionaram.

Links | Forms |
:----:|:-----:|
![Links](https://user-images.githubusercontent.com/37155530/110700583-e038d880-81ce-11eb-8f3a-f2f7d5a25fd3.png) | ![Forms](https://user-images.githubusercontent.com/37155530/110700599-e6c75000-81ce-11eb-9c96-53eba244970b.png) |


# Tarefas não Finalizadas e Justificativa

## Histórico de Revisão

Data | Versão | Descrição | Autor |
:---:|:------:|-----------|-------|
08/03|0.1 | Criação da Página | [Pedro Igor](https://github.com/pedroeagle) |
08/03|1.0 | Adição da descrição da tarefa da issue de filtro de acesso a internet. | [Pedro Igor](https://github.com/pedroeagle) |
08/03|1.1 | Adição da documentação de como publicar o app na Play Store. | [Pedro Igor](https://github.com/pedroeagle) |
09/03|1.2 | Adição da descrição da tarefa da issue de melhoria do FAQ. | [Lucas Gomes](https://github.com/LGomees) |
09/03|1.3 | Atualização da documentação de como publicar o app na Play Store. | [Pedro Igor](https://github.com/pedroeagle)|
09/03|1.4 | Adição da documentação de atualização do SDK. | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
09/03|1.5 | Finalização da documentação de como publicar o app na Play Store. | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier) |
10/03|1.6 | Adição da documentação da issue [Abrir formularios do google #9](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/9) | [Rafael Ribeiro](https://github.com/rafaelflarrn) |
10/03|1.7 | Correção de pequenos erros | [Pedro Igor](https://github.com/pedroeagle), [Geise Saunier](https://github.com/GeiseSaunier), [Rafael Ribeiro](https://github.com/rafaelflarrn), [Lucas Gomes](https://github.com/LGomees) |
15/03|1.8 | Adição de link de comentário sobre publicação do app | [Pedro Igor](https://github.com/pedroeagle)|