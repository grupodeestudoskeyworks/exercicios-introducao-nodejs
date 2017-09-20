### Lista de exercícios referente ao [post de instrodução ao Node.js](https://grupodeestudoskeyworks.github.io/posts/introducao-nodejs)

> Antes de iniciar estes exercícios garanta que você tenha instalado o **node** e o **npm** corretamente, conforme descrito no post. 

> A resolução de cada conjunto de exercícios possui sua respectiva branch neste projeto.

> Alguns exercícios propoem implementação, ou uso exitente de funções e códigos comuns, como por exemplo conversão de datas e códigos HTTP. Estes devem ser interpretados mais como um desafio para ampliar seu conhecimento, se você não se sentir a vontade em pesquisar sobre os mesmos, sinta-se a vontade para substituir por qualquer coisa coerente com o contexto. 

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
3. Crie uma rota `/agora` que retorna a data que veio do middleware anterior. A resposta deve retornar `status 200` e ter o tipo `text/plain`.
4. Crie o arquivo `util/date.js`. Nele [**exporte**](https://nodejs.org/api/modules.html#modules_module_exports) uma função com a lógica de conversão de data para string em formato ISO 8601.
5. No arquivo principal, importe a função do arquivo `util/date.js` e substitua o trecho do middleware que converte a data por sua chamada.
> **Dica**: para importa o conteúdo de um arquivo, passe para a função `require` o caminho para chegar até ele da pasta atual.

#### Criando um CRUD (sem persistência de dados)

1. Crie o arquivo `/users.js`.
2. No arquivo `/users.js`, crie uma função que recebe um objeto e um callback de sucesso que forja a inserção de um usuário, chamando o callback de sucesso com o mesmo objeto, no entanto com um id aleatório atribuido.
3. Crie uma função que forja a atualização do usuário, retornando exatamente o mesmo JSON informado. A função deverá receber os respectivos parâmetros: 
    <ul>
        <li>o id do usuário a atualizar</li>
        <li>um objeto com as informações do usuário</li>
        <li>um callback de sucesso</li>
        <li>um callback que será chamado caso aconteça algum erro</li>
    </ul>
    
    Execute as seguintes validações:
    <ul>
        <li>o id do usuário deve ser um número inteiro maior que zero</li>
        <li>o parâmetro referente ao objeto deve ser um objeto válido</li>
    </ul>
    
    Para quando uma validação falhar deve ser chamado o callback de erro passando um objeto com a mensagem do erro e o [**código HTTP do erro**](https://pt.wikipedia.org/wiki/Lista_de_c%C3%B3digos_de_estado_HTTP#4xx_Erro_de_cliente).
    
4. Crie uma função que forja a exclusão de um usuário. Ela deve receber um id e o callback de erro como parâmetros. Execute a mesma validação referente ao id do usuário.
5. Crie uma função que recebe um callback de sucesso e retorna uma lista de usuários.
6. Crie uma função que recebe um id e um callback de sucesso e que forja a busca por um usuário retornando um objeto de usuário com o mesmo id informado. 
> O formato do objeto do usuário fica a seu critério, o único requisito é que ele possua uma propriedade númerica chamada id
7. Exporte todas as funções anteriormente mencionadas.
8. No arquivo `index.js` importe as funções do arquivo `users.js`.
9. Crie as seguintes rotas:
    * `POST /users`
    * `PUT /users/:id` *
    * `DELETE /users/:id` *
    * `GET /users`
    * `GET /users/:id` * 
> \* Para posteriormente manipular os parâmetros da URL [**leia isso**](http://expressjs.com/en/4x/api.html#req).

> Para obter o JSON da requisição [**leia isso**](http://expressjs.com/en/4x/api.html#req.body). 
10. Para cada rota aplique a função correspondente importada do arquivo `/users.js`.
11. Teste cada uma das rotas com o app [POSTMAN](https://www.getpostman.com/).