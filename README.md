### Lista de exercícios referente ao [post de instrodução ao Node.js](https://grupodeestudoskeyworks.github.io/posts/introducao-nodejs)

> Antes de iniciar estes exercícios garanta que você tenha instalado o **node** e o **npm** corretamente, conforme descrito no post. 

> A resolução de cada conjunto de exercícios possui sua respectiva branch neste projeto.

#### Básico

1. Utilize o comando correto para inicializar o projeto criando o arquivo `package.json`.
2. Instale o módulo express e diga para o npm adicioná-lo como dependência no projeto.
3. Mude a versão do projeto para 0.1.0.
4. Adicione uma breve descrição ao projeto.


#### Utilizando Express

1. Importe o módulo `express` e o atribua a uma variável.
2. Crie uma rota raiz que retorne `status 200` e o texto "Sou uma aplicação express".
3. Faça com que a aplicação rode na porta 4000.
> **Dica**: você pode testar acessando o endereço http://localhost:4000 do seu browser.

#### Aplicando Middleware

1. Aplique um middleware que altera a requisição e adiciona a data atual. Essa data deve possuir o tipo `Date`.
2. Aplique um middleware que modifica a data do middleware anterior e transforme ela em uma data no formato [**ISO 8601**](https://pt.wikipedia.org/wiki/ISO_8601) como **data e horas combinadas, em UTC**.
3. Crie uma rota `/agora` que retorna a data que veio do middleware anterior. A resposta deve retornar `status 200` e um ter o tipo `text/plain`.
4. Crie o arquivo `util/date.js`. Nele [**exporte**](https://nodejs.org/api/modules.html#modules_module_exports) uma função com a lógica de conversão de data para string em formato ISO 8601.
5. No arquivo principal, importe a função do arquivo `util/date.js` e substitua o trecho do middleware que converte a data por sua chamada.
> **Dica**: para importa o conteúdo de um arquivo, passe para a função `require` o caminho para chegar até ele da pasta atual.

#### Criando um CRUD