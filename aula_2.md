BANCO DE DADOS DJANGO

Por padrão, o django usa o SQLite para as aplicações, mas podemos alterar isso em DATABASES no arquivo settings.py.

Toda nova aplicação vem ja app's convencionais para a maioria dos usos, estão listados em INSTALLED_APPS no arquivo ./settings.py, mas,
não são regras de uso, podem ser excluidos caso não venham a ser util para o projeto.

====================================
CRIANDO MODELOS DE DADOS
====================================
Um modelo é a fonte única e definitiva de informações sobre seus dados. Ela contém os campos e comportamentos essenciais dos dados que você está armazenando.

Criamos os modelos no arquivo models.py de nossos app's dentro do projeto.
Cada modelo tem um número de variáveis de classe, cada um deles representa um campo de banco de dados no modelo, e as classes representando o tipo de dados, com diversos parametros
opcionais.

Esse pequeno código de modelo dá ao Django muitas informações. Com ele, Django é capaz de:
    -Crie um esquema de banco de dados (instruções) para este app.CREATE TABLE
    -Crie uma API de acesso ao banco de dados Python para acessar os dados.

Mas primeiro, precisamos informar ao nosso projeto que este app esta instalado para ele poder considerar seu banco de dados.
Para incluir nosso aplicativos no projeto, temos que adiciona-lo na variavel de lista INSTALED_APPS em setting.py na raiz do projeto.
Incluimos la, o caminho ate a configuração do app que fica na pasta apps.py
no nosso caso seria algo como: "polls.apps.PollsConfig"

também existe a possibilidade apenas de incluir o diretorio do app, ou seja, apenas "polls", porém, é uma boa prática usar o caminho completo para evitar ambiguidades e garantir que a
configuração personalizada seja utilizada corretamente.

uma vez o configurado, temos que dizer ao django sobre atualizações ou criação de modelos no nosso app, que gostariamos que fossem armazenados como uma migração.
(migração são arquivos python que descrevem como o banco de dados deve ser alterado para refletir as mudanças feitas nos modelos do aplicativo)
para isso, precisamos executar o seguinte comando:

-- python .\manage.py makemigrations "nome do app" -- para fazer as migrações exclusivamente para aquele app
-- python .\manage.py makemigrations -- faz todas as migrações pendentes

Agora para fazer a criação dessas tabelas de modelo no banco de dados, é necessario realizar o seguinte comando:

-- python .\manage.py migrate --
    O comando pega todas as migrações ainda não aplicada (assim como as dos apps ja previamente instalados em settings, caso seja a primeira vez que roda o comando) e
    os executa em seu banco de dados.

As migrações são muito poderosas e permitem que você altere seus modelos ao longo do tempo, à medida que você desenvolver seu projeto, sem a necessidade de excluir seu banco de dados ou tabelas e fazer novos - é especializada em atualizar seu banco de dados ao vivo, sem perda de dados.


================================================================
SHELL INTERATIVO PYTHON COM API DJANGO (introdução rapida)
================================================================

Execute o seguinte comando para incovar o shell do python com a api do django incializada
--  python manage.py shell --

Isso vai permitir que interaja com seu código e banco de dados sem precisar iniciar o servidor, facilitando testes rápidos, debugging e experimentação.

✅ Manipular o banco de dados (CRUD: Create, Read, Update, Delete)
✅ Testar funções e scripts do projeto isoladamente
✅ Depurar lógicas sem precisar rodar a aplicação
✅ Interagir com autenticação e permissões
✅ Executar requisições simuladas (testes de API)

Exemplo basico de uso:
>>> from polls.models import Choice, Question
>>> Question.objects.all()
<QuerySet []>
>>> from django.utils import timezone
>>> q = Question(question_text="What's new?", pub_date=timezone.now())
>>> q.save()
>>> q.id
1
>>> q.question_text
"What's new?"
>>> q.pub_date
datetime.datetime(2025, 2, 10, 15, 16, 27, 725976, tzinfo=datetime.timezone.utc)
>>> q.question_text = "chama?"
>>> q.save()
>>> q.question_text
'chama?'
>>> Question.objects.all()
<QuerySet [<Question: chama?>]>
# Procurar uma questão com filtro
>>> current_year = timezone.now().year
>>> Question.objects.get(pub_date__year=current_year)

Para mais usos verificar a documentação



