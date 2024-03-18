Univesidade Lusófona
**Programação Web**

# Ficha 5: Modelação e Manipulação de dados em Django

### Objetivo:
* familiarizar-se com a modelação e manipulação de modelos Django.
* Criar um projeto django diretamente no PythonAnywhere seguindo os passos apresentados na aula teória. Use como username o seu número.
* Criar várias aplicações, centrando-se apenas na modelação e criação de alguns conteúdos usando a aplicação admin do Django, interface de administração da base de dados.
* Criar scripts que façam manipulação de dados.
 
<!--
### 0. Aplicação Pessoas no PC

* siga os passos do [tutorial](pw-24-04-criacao-de-app-no-pc.pdf) para criar uma primeira aplicação em Django no seu PC
-->


### 1. Exercícios de métodos ORM

Crie uma aplicaçãoo com os seguintes modelos:

```Python
from django.db import models

class Autor(models.Model):
    nome = models.CharField(max_length=100)
    data_nascimento = models.DateField()
    nacionalidade = models.CharField(max_length=100)

    def __str__(self):
        return self.nome

class Livro(models.Model):
    titulo = models.CharField(max_length=200)
    data_publicacao = models.DateField()
    autor = models.ForeignKey(Autor, on_delete=models.CASCADE)
    genero = models.CharField(max_length=100)

    def __str__(self):
        return self.titulo

class Leitor(models.Model):
    nome = models.CharField(max_length=100)
    email = models.EmailField()
    data_associacao = models.DateField()

    def __str__(self):
        return self.nome

class Emprestimo(models.Model):
    livro = models.ForeignKey(Livro, on_delete=models.CASCADE)
    leitor = models.ForeignKey(Leitor, on_delete=models.CASCADE)
    data_emprestimo = models.DateField()
    data_devolucao = models.DateField(null=True, blank=True)

    def __str__(self):
        return f"{self.leitor} emprestou {self.livro}"
```

Implemente instruções que façam o seguinte:

* Recuperar todos os autores de uma nacionalidade específica.
* Encontrar o número total de livros emprestados por um determinado leitor.
* Listar todos os livros emprestados a um leitor com um determinado endereço de e-mail.
* Encontrar todos os livros publicados após uma data específica.
* Recuperar todos os livros com seus autores e gêneros.
* Listar todos os leitores que emprestaram livros publicados antes de 2010.
* Encontrar o número de livros em cada gênero.
* Listar todos os leitores que ainda não devolveram os livros emprestados.
* Recuperar o autor de um livro específico.
* Listar todos os leitores que emprestaram livros escritos por autores de uma nacionalidade específica.

### 2. Manipulação do modelo das bandas

Para a modelação das bandas que realizou na ficha anterior, redija um conjunto de perguntas sobre os dados às quais deverá responder usando os métodos ORM que aprendeu. Crie pelo menos 10 perguntas que explorem todos os métodos do ORM Django. Exemplos de perguntas: 
* listar o nome dos álbuns de uma banda, ordenados cronológicamente
* apresentar todos os álbuns lançados em 2020
* uma playlist de um album, i.e., a lista dos links das músicas.
* listar os albuns com músicas que durem mais de 5 minutos
* listar os albuns com capa

### 3. Aplicação curso (componente do projeto parte 1)

A modelação que desenvolverá será usada na parte 1 do seu projeto, que será o seu portfólio.

A Lusófona tem endpoints que fornecem informação no formato JSON sobre os seus cursos. Está disponível neste repositório informação sobre os cursos de [LEI](lei.json) e [LIG](lig.json). Analise o conteúdo do JSON, que se encontra renderizado na página de [LEI](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares) e de [LIG](https://informatica.ulusofona.pt/ensino/licenciaturas/engenharia-informatica/).

Crie uma aplicação que modele o seu curso (LEI ou LIG):
* crie a classe curso com os elementos mais interessantes do curso (apresentação, objetivos, competências).
* crie uma classe área cientifica. Uma disciplina tem uma área científica.
* crie uma classe para as disciplinas, onde armazenará informação da disciplina (nome, ano, semestre, ects e curricularIUnitReadableCode). Inclua um campo para a área científica da disciplina (veja áreas na página do [curso](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares).
* Crie uma classe projeto que permita registar informação sobre o projeto que fez para uma determinada disciplina (uma disciplina tem um único projeto). Sugere-se que tenha os atributos dos projetos do [DEISI](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares/), tais como descrição, conceitos aplicados da disciplina, informação de tecnologias usadas, imagem, link para um video demonstrativo de 1 minuto no yotube, incluindo também link para o repositório GitHub do projeto, caso exista. 
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
