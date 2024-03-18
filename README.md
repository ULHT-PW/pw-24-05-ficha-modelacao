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

### 1. Aplicação Pessoas no PythonAnyWhere

* siga os passos do [tutorial](pw-24-04-criacao-de-app-em-pythonanywhere.pdf) para criar uma primeira aplicação em Django diretamente no PythonAnyWhere

### 2. Aplicação bandas

* seguindo os passos dos slides anteriores, a partir da parte 3 (slide 19), crie uma nova aplicação **bandas**:
   1. `python manage.py startapp bandas`
   1. em `project\settings.py`, adicione à lista `INSTALLED_APPS` a aplicação `bandas`. 
* em models.py, crie um conjunto de classes que permitam definir bandas, seus álbuns e músicas. No final, não se esqueça de:
   * registar cada uma das classes em admin.py
   * migrar as alterações com makemigrations e migrate
   * relançar a aplicação
* Em relação a cada classe, crie um conjunto de atributos. Sugestões:
   * guarde para cada álbum uma capa
   * para algumas músicas guarde o link da música no spotify
   * guarde uma foto da banda, e informações variadas
* faça os passos makemigrations e migrate para migrar o models para a base de dados 
* crie conteúdos de um par de bandas e seus discos e músicas através da aplicação admin.
* configure a aplicação admin de modo a listar informação util e permitir pesquisas adequadas.

Nota: daqui a algumas semanas irá construir a parte de front-end desta aplicação.

### 3. Aplicação artigos

Crie uma aplicação que permita armazenar artigos de vários autores. Inspire-se em blogs que conheça de modo a fazer uma modelação rica. deverá permitir, além dos posts, inserir comentários, e ratings. Insira 2 artigos, por exemplo, do blog medium ou Quora. 

Esta aplicação será integrada no seu projeto final, o seu protfolio. vAqui incluirá artigos que considera interessantes ligados com a Programação Web.

# Submissão

submeta o link da sua aplicação, assim como as credenciais de um superuser para aceder ao admin (username e password). Pode criar vários superusers

<!-- 

### 4. Aplicação curso (a desenvolver até 21.3)

crie uma aplicação que permita definir um curso, suas disciplinas, seus docentes e projetos. Inspire-se nesta [página](https://informatica.ulusofona.pt/projetos-de-unidades-curriculares) e [nesta](https://informatica.ulusofona.pt/ensino/licenciaturas/engenharia-informatica/)

Algumas ideias:
* uma disciplina tem um conjunto de docentes
* um docente pode lecionar várias disciplinas
* uma disciplina tem um conjunto de informações tais como ano, semestre, programa.
* uma disciplina pode ter um ou mais projetos
* cada projeto pode ter descrição, imagem, url para repo no github, informação de tecnologias usadas, um link para um video no yotube.
* configure a aplicação admin de modo a listar informação util de cada classe e permitir pesquisas adequadas.
* crie conteúdos de um par de disciplinas e seus projetos. Na proxima semana ser-lhe-ão facultados dados detalhados de seu curso e respetivas disciplinas, e implementará uma função para carregar esta informação na sua base de dados de forma automática.

Esta aplicação será integrada no seu projeto final, o seu protfolio. Será uma excelente carta de apresentação em entrevistas de emprego que permitirá mostrar os projetos que desenvolveu ao longo do seu curso.




### 5. Aplicação Mentoria

O Programa de Mentoría é um programa do DEISI de alunos para alunos, suportado por uma [aplicação](https://horarios.pythonanywhere.com/) em desenvolvimento no âmbito dum TFC. Explore a aplicação, fazendo login e pedindo recuperação da sua password com o email que está no Moodle. 

Esta aplicação congregará artigos que considera interessantes, na área da programação web.

Crie uma aplicação que modele o programa de mentorias. Algumas ideias:
* um aluno pode ser mentor/mentorando de uma ou mais disciplinas
* uma díade é um par (mentor,mentorando), que realiza sessões de mentoria em dias específicos
* configure a aplicação admin de modo a listar informação util de cada classe e permitir pesquisas adequadas.
-->
