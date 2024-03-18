Univesidade Lusófona
**Programação Web**

# Ficha 5: Modelação em Django

### Objetivo:
* familiarizar-se com a modelação e manipulação de modelos Django.
* Criar um projeto django diretamente no PythonAnywhere seguindo os passos apresentados na aula teória. Use como username o seu número.
* Criar várias aplicações, centrando-se apenas na modelação e criação de alguns conteúdos usando a aplicação admin do Django, interface de administração da base de dados.
* Criar scripts que façam manipulação de dados.
 
<!--
### 0. Aplicação Pessoas no PC

* siga os passos do [tutorial](pw-24-04-criacao-de-app-no-pc.pdf) para criar uma primeira aplicação em Django no seu PC
-->

### s

Considere os seguintes modelos:

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


### 1. Manipulação do modelo das bandas

Para a modelação das bandas que realizou na ficha anterior, redija um conjunto de perguntas sobre os dados às quais deverá responder usando os métodos ORM que aprendeu. Crie 10 perguntas que explorem todos os métodos. Exemplos de perguntas: 
* listar o nome dos álbuns de uma banda, ordenados cronológicamente
* apresentar todos os álbuns lançados em 2020
* uma playlist de um album, i.e., a lista dos links das músicas.
* listar os albuns com músicas que durem mais de 5 minutos
* listar os albuns com capa

### 2. Aplicação curso (componente do projeto parte 1)

A modelação que desenvolverá será usada na parte 1 do seu projeto, que será o seu portfólio.

A Lusófona tem endpoints que fornecem informação no formato JSON sobre os seus cursos. Está disponível neste repositório informação sobre os cursos de [LEI](lei.json) e [LIG](lig.json). Analise o conteúdo do JSON, que se encontra renderizado na página de [LEI](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares) e de [LIG](https://informatica.ulusofona.pt/ensino/licenciaturas/engenharia-informatica/).

Crie uma aplicação que modele o seu curso (LEI ou LIG), modelando e extraindo os elementos que considera mais interessantes (apresentação, objetivos, competências, entre outros) e as suas disciplinas.

Deverá criar uma classe para as disciplinas, onde armazenará informação

Crie uma classe projeto que tenha os atributos dos projetos do [DEISI](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares/) e esteja associada à classe disciplina assim como linguagem de programação (relação MAnyToMany, pois por exemplo em Programação Web aprenderá várias linguagens).



Faça uma 

Algumas ideias:
* uma disciplina tem um conjunto de informações tais como ano, semestre, programa.
* uma disciplina tem um conjunto de docentes.
* um docente pode lecionar várias disciplinas.
* uma disciplina pode ter um ou mais projetos.
* cada projeto pode ter uma descrição, conceitos aplicados da disciplina, informação de tecnologias usadas, imagem, link para um video no yotube e url para repo no github.
* explore as configurações do interface web /admin, de modo a listar informação util de cada classe e permitir pesquisas adequadas.
* Extraia dados do seu curso e respetivas disciplinas, e implemente uma função para carregar esta informação na sua base de dados de forma automática.
* crie um script que integra um conjunto de instruções que exploram os métodos que aprendeu na aula, para extrair informação da base de dados. 

Esta aplicação será integrada no seu projeto final, o seu protfolio. Será uma excelente carta de apresentação em entrevistas de emprego onde poderá mostrar os projetos que desenvolveu ao longo do seu curso.

<!--
### 2. Aplicação Mentoria

O Programa de Mentoría é um programa do DEISI de alunos para alunos, suportado por uma [aplicação](https://horarios.pythonanywhere.com/) em desenvolvimento no âmbito dum TFC. Explore a aplicação, fazendo login e pedindo recuperação da sua password com o email que está no Moodle. 

Esta aplicação congregará artigos que considera interessantes, na área da programação web.

Crie uma aplicação que modele o programa de mentorias. Algumas ideias:
* um aluno pode ser mentor/mentorando de uma ou mais disciplinas
* uma díade é um par (mentor,mentorando), que realiza sessões de mentoria em dias específicos
* configure a aplicação admin de modo a listar informação util de cada classe e permitir pesquisas adequadas.
-->

# Submissão

submeta o link da sua aplicação, assim como as credenciais de um superuser para aceder ao admin (username e password). Pode criar vários superusers
