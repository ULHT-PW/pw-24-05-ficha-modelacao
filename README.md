Univesidade Lusófona
**Programação Web**

# Ficha 5: Modelação e Manipulação de dados em Django

### Objetivo:
* familiarizar-se com a modelação e manipulação de modelos Django.
* Exercitar a manipulação de dados
* trabalhar na aplicação bandas que desenvolveu.
* Criar várias aplicações, centrando-se apenas na modelação e criação de alguns conteúdos usando a aplicação admin do Django, interface de administração da base de dados.
* Criar scripts que façam manipulação de dados.
 
<!--
### 0. Aplicação Pessoas no PC

* siga os passos do [tutorial](pw-24-04-criacao-de-app-no-pc.pdf) para criar uma primeira aplicação em Django no seu PC
-->


### 1. Django ORM... Quiz Time!

Exercite os métodos de ORM Django respondendo ao [Quizz](https://djangoorm.pythonanywhere.com/). 


### 2. Manipulação do modelo das bandas

1. Veja o [Tutorial de importação de ficheiros JSON na BD duma webApp](https://github.com/ULHT-PW/importar-json)
1. Veja os [detalhes de utilização dos campos ImageField e FileField num modelo](https://github.com/ULHT-PW/pw-usando-ImageField) (até ao ponto 4)

Copie a modelação das bandas que realizou na ficha anterior e partilhe-a no ChatGPT para que o ajude a ampliar a base de dados. Peça-lhe para criar um JSON com 10 bandas de um género que gosta (por exemplo rock, ou funck, ou pop), pedidno para que identifique a nacionalidade e ano de criação da banda. Peça para criar outro JSON com uma lista de pelo menos 20 discos dessas bandas, tendo para cada disco o titulo, ano do lançamento e a lista de musicas, incluindo o titulo e a duração.

Carregue estes ficheiros na base de dados usando uma função num script (ficheiro python). Use o módulo json falado na aula (veja os slides). Deverá executar este script através da shell do django, que lança desta forma:

```Bash
> python manage.py shell
```

Na shell, importe models e o script, e execute a função, considerando que o ficheiro json está na pasta do script:
```Python
>>> from curso.models import *
>>> import script_importacao.py
>>> importar_curso("lei.json")
```

Redija 10 perguntas, às quais deverá responder usando os métodos ORM que aprendeu. Experimente os métodos na Shell do django. Exemplos de perguntas: 
* listar o nome das bandas, ordenadas alfabéticamente
* listar o nome dos álbuns de uma banda, ordenados cronológicamente
* apresentar todos os álbuns que foram lançados entre dois anos à sua escolha.
* criar uma playlist de um album, i.e., a lista dos links das músicas.
* listar os albuns com músicas que durem mais de 5 minutos
#* listar todas as músicas que tenham uma determinada palavra

Irá desenvolver daqui a umas semanas ainda mais esta aplicação, criando uma página de bandas de um estilo que gosta, integrando um player.

### 3. Aplicação curso (componente do projeto parte 1)

A modelação que desenvolverá neste exercício será parte constituinte na parte 1 do seu projeto, que será o seu portfólio.

A Lusófona tem endpoints que fornecem informação no formato JSON sobre os seus cursos. Está disponível neste repositório informação sobre os cursos de [dados em JSON sobre LEI](lei.json) e [dados em JSON sobre LIG](lig.json). Analise o conteúdo do JSON, que se encontra renderizado na [página de LEI](https://informatica.ulusofona.pt/ensino/licenciaturas/engenharia-informatica/) e na [página de LIG](https://informatica.ulusofona.pt/ensino/licenciaturas/informatica-de-gestao/).

Crie uma aplicação que modele o seu curso (LEI ou LIG):
* crie a classe curso com os elementos mais interessantes do curso (apresentação, objetivos, competências).
* crie uma classe área cientifica. Uma disciplina tem uma área científica.
* crie uma classe para as disciplinas, onde armazenará informação da disciplina (nome, ano, semestre, ects e curricularIUnitReadableCode). Inclua um campo para a área científica da disciplina (veja o separador áreas na página do [curso](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares)).
* Crie uma classe projeto que permita registar informação sobre o projeto que fez para uma determinada disciplina (uma disciplina tem um único projeto). Sugere-se que tenha os atributos dos [projetos de UCs do DEISI](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares/), tais como descrição, conceitos aplicados da disciplina, informação de tecnologias usadas, imagem, link para um video demonstrativo de 1 minuto no yotube, incluindo também link para o repositório GitHub do projeto, caso exista. 
* crie uma classe linguagem de programação. Lembre-se que nalgumas disciplinas e projetos utiliza mais do que uma linguagem de programação. Referencie nos projetos as linguagens usadas.
* crie uma classe docente. Uma disciplina tem um conjunto de docentes, e um docente pode lecionar várias disciplinas.

Em relação à visualiação no interface web /admin:
* explore as configurações do interface web /admin, de modo a listar informação util de cada classe e permitir pesquisas adequadas.
* Extraia dados do seu curso e respetivas disciplinas, e implemente uma função para carregar esta informação na sua base de dados de forma automática.
* crie um script que integra um conjunto de instruções que exploram os métodos que aprendeu na aula, para extrair informação da base de dados. 

Escreva um script, script_importacao.py, com a função importar_curso(ficheiro_json) que servirá para importar os dados do curso para a base de dados. Para o utilizar deverá abrir a shell:

```Bash
> python manage.py shell
```

Na shell importar os modelos, o script, e correr a função, considerando que o ficheiro json está na pasta do script:
```Python
>>> from curso.models import *
>>> import script_importacao.py
>>> importar_curso("lei.json")
```

Esta aplicação será integrada no seu projeto final, o seu protfolio. Será uma excelente carta de apresentação em entrevistas de emprego onde poderá mostrar os projetos que desenvolveu ao longo do seu curso.


# Submissão

submeta o link da sua aplicação, assim como as credenciais de um superuser para aceder ao admin (username e password). Pode criar vários superusers
