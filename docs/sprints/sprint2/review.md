# Revisão

Tarefa | Finalizada? |
:-----:|:-----------:|
[Filtrar acesso a internet antes de abrir o WebView](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/5) | :heavy_check_mark: |
[Documentar todo o processo de publicação do app na Google Play e Apple Store](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/6)| :heavy_check_mark: |
[Melhorar FAQ](https://github.com/GCES-Escola-em-Casa-2020-2/wiki/issues/3)| :heavy_check_mark: |

# Tarefas

## Filtrar acesso a internet antes de abrir o WebView

Foi criada uma tela informando que o usuário está sem acesso a internet. Além disso foi adicionado um botão para que o usuário tente se conectar novamente. O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/55).

## Documentar todo o processo de publicação do app na Google Play e Apple Store

A última etapa do processo é de fato submeter a aplicação para revisão e publicação na Play Store. É necessário criar uma conta no [Google Play Console](https://play.google.com/console/signup) preenchendo todas as informações do desenvolvedor. 

Após criada a conta, basta clicar em "Criar app" na primeira página. Será necessário preencher vários metadados do app tais como faixa etária do público alvo, restrições de idade, categoria do conteúdo, contas para que a equipe da Google possa testar, configurações de anúncios, submissão de certificado de privacidade dentre outros. 

Algumas configurações a serem especificadas são mostradas como pendentes ao clicar na opção "Produção" ou "Teste" a depender do tipo de submissão que será realizado, na barra lateral. Nessa mesma página é possível selecionar o APK (arquivo executável do aplicativo, em formato .apk) ou um arquivo em formato .aab (Android App Bundles). Também é possível especificar a versão do app além de diversas descrições que aparecerão na página do aplicativo. É obrigatória a submissão de um banner e alguns prints da aplicação em funcionamento. É, inclusive, recomendado que o nome desses arquivos de imagem sejam significativos para que sejam sugeridos em pesquisas do Google, aumentando assim o alcance do app. Após toda essa etapa de detalhamento do aplicativo basta clicar em "Iniciar lançamento para Produção". 

Para lançar uma nova versão da aplicação basta selecioná-la no Painel inicial do Google Console e clicar em "Criar nova versão".

Como se trata de uma aplicação que utiliza serviço de VPN é necessário tomar alguns cuidados para que a publicação seja aceita. Na documentação do Datami é sugerida a importação da lib por meio do gerenciador de pacotes Maven da seguinte forma:

**(Exemplo de como não deve ser feito)**
```
maven {
 url 'https://s3.amazonaws.com/sdk-gareleases.cloudmi.datami.com/android/mvn/smisdk/'
}
 ```
 **PORÉM AO REALIZAR ESSA IMPORTAÇÃO A APLICAÇÃO SERÁ RECUSADA PELA EQUIPE DA GOOGLE.**

 A forma "correta" de realizar essa a importação da lib é baixando o arquivo mais atual no [Site do Datami](https://developer.datami.com/#/onboardhome/sdkintegrationkit). É necessária uma conta que pode ser criada gratuitamente. Basta selecionar "android" em seguida a versão mais atual e então baixar o arquivo "vpnsdk-android.zip", após extraído será encontrado um arquivo em formato ".aar". O arquivo deve ser adicionado ao diretório "app/libs" no diretório raiz. Dele virão todos os métodos necessários para a utilização do Datami.

 Além de alguns cuidados com APIs externas que podem ser prejudiciais pode ser necessária a submissão de alguns certificados e resposta de questionários informando tudo o que é realizado e como é feito para a publicação seja aceita.

## Melhorar FAQ

Os comentários sobre o aplicativo foram analisados e posteriormente criamos mais algumas dúvidas na página de 'Dúvidas Frequentes'. Além disso, foi criada uma RecyclerView para remodelar o formato de como as dúvidas e respostas eram mostradas na tela. Com a implementação dessa view, os usuários podem visualizar todas as dúvidas cadastradas, e podem clicar em cima de cada uma para visualizar sua respectiva resposta. O PR foi aberto no repositório oficial e está disponível [aqui](https://github.com/Escola-em-Casa/android-escola-em-casa/pull/56)

# Tarefas não Finalizadas e Justificativa

## Histórico de Revisão

Data | Versão | Descrição | Autor |
:---:|:------:|-----------|-------|
08/03|0.1 | Criação da Página | [Pedro Igor](https://github.com/pedroeagle) |
08/03|1.0 | Adição da descrição da tarefa da issue de filtro de acesso a internet. | [Pedro Igor](https://github.com/pedroeagle) |
08/03|1.1 | Adição da documentação de como publicar o app na Play Store. | [Pedro Igor](https://github.com/pedroeagle) |
09/03|1.2 | Adição da descrição da tarefa da issue de melhoria do FAQ. | [Lucas Gomes](https://github.com/LGomees) |
09-03|1.3 | Atualização da documentação de como publicar o app na Play Store. | [Pedro Igor](https://github.com/pedroeagle)|
