
# Projeto em nodeJs com TS
## Tutórial básico

<p style=color:yellow;font-style:italic>o objetivo desse material e ser um guia básico, para você poder seguir com seu projeto e estudos sobre TS.<p>

<p>
Olá peoples, ai vai um pequeno roteiro do processo de criação de um projeto em nodeJs com typescrit.
</p>

***primeira coisa instalar o tyepescript ( esse processo é feito uma única vez )***

```bash
    npm install -g typescript   ( para usa o windows )

    npm install -g typescript   ( para quem usa linux ou mac )
```    

***agora vamos escolher o local e criar a pasta do projeto***

- dentro da pasta iniciar as devidas istalações 

    - cria com as configurações default automaticamente PACKAGE.JSON
    ```bash
    npm init -y
    ```   
    - instalar o typescript como dependência de desenvolvimento 
    ```bash
    npm i typescript -D         
    ```

    - instalar o pacote de tipagem para o nodeJs 
    ```bash
    npm i @types/node -D        
    ```

    - criar o arquivo de configuração do typescript TSCONFIG.JSON 
    ``` bash 
    npx tsc --init
    ```              
  - Como deve ficar o seu arquivo TSCONFIG.JSON (básico)

 ```JSON
  {
    "compilerOptions": {
        "target": "es6",       
        "module": "commonjs", 
        "sourceMap": true,    
        "outDir": "./build",  
        "rootDir": "./src",        
        "removeComments": true,    
        "noImplicitAny": true,     
        "noEmitOnError": true,     
     }
}
```

  - dentro da pasta do seu projeto ( na raiz do projeto )
    - creie as pastas:  <span style=font-size:19px> src</span> e
    <span style=font-size:17px>build</span>.


- Transpilando um arquivo escrito em typescript

  ```bash
    npx tsc nome-do-arquivo.ts
  ```
- após a transpilação é gerado um arquivo de mesmo nome sendo .js
  - para executar o arquivo criado use:

```bash
  node nome-do-arquivo
```
- automatizando a transpilação e execução do código 
  - pra isso precisa criar script que vão transpilar
  - e em seguida rodar nosso código
- veja no exemplo abaixo o start 
  - tsc transpila os arquivos que estão na pasta src
  - node ./build/index.js executa o arquivo .js que 
    foi resultado da transpilação.
```json
{
   "name": "exemplo",
   "version": "1.0.0",
   "description": "",
   "main": "index.js",
   "scripts": {
		 "start": "tsc && node ./build/index.js"
   },
   "keywords": [],
   "author": "",
   "license": "ISC"
}
```
  <p style=color:yellow>com isso podemos estudar as tipagens</p>

## COMPLEMENTO ( NECESSÁRIO PARA O PROJETO )

  - instalar o express  
```bash
    npm install express   
```
  - tipagem para express 
```bash
    npm install @types/express -D 
```
  - cors, permite enviarmos requisições entre back e front no mesmo pc  
```bash
    npm install cors     
```         
  - typagem para o cors 
```bash
    npm install @types/cors -D    
```
  - permite executar o ts diretamente
```bash
    npm install ts-node-dev -D    
```
  - knex - manipulador de banco de dados + typagem
```bash
    npm install knex sqlite3      
    npm install -D @types/knex    
```


## Primeiros passos no typescript

### typagens

#### variáveis:

```ts
    //um só tipo (const ou let)

    // tipo string
    let name:string = "bart"

    // tipo number
    let age:number = 20

    // tipo boolean
    let valid:boolean = true

    /* e se precisar de mais de um tipo? 
    (ai faz sentido ser let )*/
     
    /* essa forma de declarar é 
     union types = união de tipos ) */
    let example:string|number    

    // se for um array comum ?

     // array de strings uma forma
     const names:string[] = ["eu","tú","ele"] 

     // array de strings  outra forma
     const names:Array<string> = ["eu","tu","ele"]  
  
     // um array de strings e números uma forma 
     const mix:(string|number)[] = ["eu",10,"tu",10]       

     // um array de strings e números outra forma )
     const mix:Array<string|number> = ["eu",10,"tu",10]    

    
    //se for um objeto ?
    
    // faz a tipagem das chaves em seguida  atribui os valores    
    const person: { name: string, age: number} = 
                  { name: "Bart", age: 55}

   // se for um array de objetos 

    /* apenas como exemplo a forma ideal é utilizar 
     a interface (mostrada abaixo) */ 
    const person: { name: string, age: number}[] = 
    [{name: "Bart", age: 55}, {name: "Silva", age: 55}] 

    // criar a interface (  modelo, molde, padrão )
    interface Person { 
        name: string
        age: number
    }

    // agora aplica ao array de objetos o padrão (interface) 

    const person: Person[] = [
      {
        name: "Bart",
        age: 55
      },
      {
        name: "Silva",
        age: 55
      }
    ] 

    /* Similar a interface temos o type 
       observe que em interface não usa o ( = ) nem a ( , ) 
       no type usa.*/

    type Person = {
        name: string,
        age: number
    }

    /* Importante sobre type posso 
       fazer Intercessões ( combinar tipos )*/

    type User = {
        username: string
    }
    
    // criando o tipo account (juntando Person e User)
    type account = Person & User

// mais um tipo de dado interessante

    /* Enum - serve para criar dados que 
       tem valores pré-definidos.

       nomenclatura pode ser PascalCase ou UPPER_CASE
     */

    // declarando um Enum     
    enum SCHEDULE_CLASSES {
    MANHA = "Manhã",
    TARDE = "Tarde",
    NOITE = "Noite"
    }

    // como usar? ( tipar )

    // criando interface utilizando o enum SCHEDULE_CLASSES
    interface Student {
        name: string,
        year: string,
        shift: SCHEDULE_CLASSES
    }

    // criando arrray de objetos tipo Student 

    // utiliando o Enum
    const students:Student[] = [{name:"Sabtudo",year: "oitavo ano",shift:SCHEDULE_CLASSES.MANHA}]

```

** espero que de alguma forma te ajude no processo **

    


 

    
  
    


 
