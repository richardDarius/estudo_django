INICIAR UM PROJETO
existem duas maneiras, que no final so mudam os nomes dos diretorios, afim de organização

--- django-admin startproject meusite
    Cria um diretorio novo no diretorio que você ja se encontra, com um projeto que tem o mesmo nome do diretorio novo, essa pasta de projeto
    lida com as configurações do seu projeto com arquivos criados automaticamentes, a diferença desse metodo é que o nome da pasta de configuração tera o mesmo nome
    do diretorio de criação, pois ele criara abmso
    resultado:
        desktop/diretorio_atual/ meusite <-- diretorio criado para ter o projeto  /meusite <-- pasta projeto

--- django-admin startproject meusite "diretorio_existente"
    esse cria seu projeto dentro do diretorio que ja existe, no nosso caso, "ESTUDOS" então ele criou o projeto meusite,
    dentro desse diretorio na area de trabalho, a diferença é que fica menos pastas dentro de um unico diretorio e com nomes separados
    esse comando é recomendavel fazer na area de trabalho, ja que ele vai olhar o diretorio existente e criar o projeto la
    resultado:
       desktop/diretorio_existente/meusite <-- pasta projeto

(o segundo comando deixa as coisas menos confusas pra aprender do que o primeiro, ja que só vai criar uma unica pasta nova, sendo ela, o projeto em si)

apos um dos comando a cima, o diretorio escolhido tera os seguintes arquivos e pacotes:

    manage.py: Um utilitário de linha de comando que permite interagir com este Projeto Django de várias maneiras.

    meusite/: Um diretório que é o pacote Python real para o seu projeto. Seu nome é o nome do pacote Python que você precisará usar para importar qualquer coisa dentro dele (por exemplo).meusite.urls

    meusite/__init__.py: Um arquivo vazio que informa ao Python que este deve ser considerado um pacote Python. Se você é um iniciante em Python, leia mais sobre pacotes nos documentos oficiais do Python.

    meusite/settings.py: Configurações/configuração para este Django projeto. As configurações do Django informarão tudo sobre como as configurações de trabalho.

    meusite/urls.py: As declarações de URL para este projeto Django; um "índice" do seu site com Django.

    meusite/asgi.py: Um ponto de entrada para servidores web compatíveis com ASGI para servir seu projeto. 

    meusite/wsgi.py: Um ponto de entrada para servidores Web compatíveis com WSGI para servir seu projeto.

Ele também ja tera disponibilidade de rodar um servidor, para isso, mude para o diretorio raiz no terminal de comando, no nosso caso "estudos" e la rode o seguinte comando
---  python manage.py runserver
    E então o servidor rodara localmente porta 8000, por enquanto nao tem configuração alguma, nem sequer banco de dados, mas ja serve de exemplo.

CRIAÇÃO DO PRIMEIRO APP DO PROJETO:

definição:
    Um projeto é uma coleção de configuração e aplicativos para um site específico. Um projeto pode conter vários aplicativos. Um aplicativo pode estar em vários projetos.

--- python manage.py startapp "nome do app"
    Inicia um app django

O aplicativo ja vem com uma estrutura de diretorios criada, para focarmos apenas em codigo.

urls.py (necessario incluir manualmente no diretorio do app do django):
em projeto/app/urls.py precisamos incluir as views criadas em nosso views.py que serão apresentadas em determinadas rotas com um path(rota,views,name da view).
ja na raiz, em projetos/urls.py precisamos mapear o roteamento de urls passando a funcção include('app.urls') para incluir urls do app criado anteriormente no projeto,
isso vai permitir que o app gerencie suas propias rotas.

entao a rota sera algo como:

     localhost:8000/app/rota_url_app 

"app" é a rota incluida em urls.py do diretorio do projeto, e "rota_url_app" a rota do urls.py do diretorio do app
primeiro ele acessa a rota registrada no projeto, no caso "polls", pra saber que é pra redirecionar para as rotas registradas do app (app = polls no caso)
