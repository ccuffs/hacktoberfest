# Tutorial básico de git

Esse é um tutorial super básico para ensinar a ideia geral do [git](https://git-scm.com/) e de [controle de versão](https://pt.wikipedia.org/wiki/Sistema_de_controle_de_vers%C3%B5es).

## Crie uma conta no Github

Você não precisa de uma conta no [Github](https://github.com) para usar git, mas para esse tutorial ela será utilizada. Criar uma conta no [Github](https://github.com) é grátis.

> **DICA:** como nome de usuário para sua conta (_username_), escolha algo que você não tenha vergonha de mostrar a um futuro empregador. Ex.: `FulanoSilva` é melhor que `cristalRoxoGamer12`. 

## Instalando o git na sua máquina

Veja se o git já não está instalado rodando o seguinte:

```
git --version
```

Se você ver alguma coisa como `git version 2.7.4` no terminal, o git está instalado e pronto para usar. Se esse não for o caso, rode (no Ubuntu):

```
sudo apt-get install git
```

## Configurando o git

É muito importante que seus dados de desenvolvedor (nome, e-mail, etc) estejam corretamente informados para o git usar. Essas informações aparecerão no histórico de versões do seu projeto (e para seus colegas desenvolvedores).

Para alterar o seu *nome*, rode o seguinte (troque `Fulano da Silva` pelo seu nome):

```
git config user.name "Fulano da Silva"
```

Para alterar o seu *e-mail*, rode o seguinte (troque `fulano@silva.com` pelo seu e-mail):

```
git config user.email "fulano@silva.com"
```

Para ver quais as informações o git tem gravado, rode:

```
git config --list
```

## Criando um repositório no Github

Acesse [github.com](https://github.com) e efetue login com seu usuário e senha. Depois, clique no botão com um `+` (no canto superior direito da tela) e escolha `New repository`.

Na tela para criar um novo repositóio, escolha um nome para ele, se ele é publico (todos tem acesso) ou privado (somente você tem acesso), e se ele deve ser inicializado com um conteúdo inicial (geralmente um arquivo README).

Por fim, clique no botão verde `Create repository` para criar seu repositório.

## Baixando o repositório para sua máquina (clonar o respositório)

Depois que o repositório for criado no [Github](https://github.com), precisamos baixar ele para a sua máquina. Essa operação é chamada de `git clone`.

Ao clicar no botào `Clone or download` do respositório, você pode escolher qual URL deseja usar. Para esse tutorial, vamos escolher a URL com `HTTPS`. Copie essa URL.

Em seguida, navegue até a pasta do seu computador onde o repositório será baixado. É comum colocar repositórios na home do seu usuário:

```
cd ~/
```

Depois de navegar até a pasta, clone o respositório:


```
git clone COLE_AQUI_A_URL_QUE_VOCE_COPIOU_ANTES
```

No comando acima, você precisa substituir `COLE_AQUI_A_URL_QUE_VOCE_COPIOU_ANTES` pela URL do seu repositório. No caso desse tutorial, essa URL é `https://github.com/Dovyski/teste.git`:

```
git clone https://github.com/Dovyski/teste.git
```

Depois de rodar esse comando, o git pedirá seu ***username*** (não e-mail!) e ***senha** de acesso ao Github. Informe ele para poder acessar o repositório.

Se tudo estiver certo, você verá algo parecido com isso:

```
fernando@lenovo-fernando:/tmp$ git clone https://github.com/Dovyski/teste.git
Cloning into 'teste'...
Username for 'https://github.com': dovyski
Password for 'https://dovyski@github.com':
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```

Nesse caso, o git criará a pasta `teste` no seu computador (porque o respositório se chama `Dovyski/teste`). Essa pasta `teste` está conectada com seu repositório online. 

Acesse a pasta:

```
cd teste
```

> *Dica:* você pode escolher o nome da pasta que o git cria usando `git clone URL NOME_PASTA`, ex.: `git clone https://github.com/Dovyski/teste.git abobrinha` clonará o respositório para uma pasta chamada `abobrinha`.

## Salvando seu e-mail e senha do Github

Para não termos que digitar o e-mail e senha em todos os comandos, vamos pedir para o git salvar essas informações.

Rode:

```
git config credential.helper store
```

Depois, rode:

```
git pull
```

Novamente o git pedirá seu ***username*** (não e-mail!) e ***senha** de acesso ao Github. Informe eles corretamente, pressione enter, e o git salvará as credenciais.

> *Dica:* a melhor forma de autenticação é usando [chaves de SSH](https://help.github.com/en/articles/connecting-to-github-with-ssh). Como isso demanda mais passos de configuração, não utilizaremos SSH para esse tutorial. Tenha em mente, porém, que acesso por [chaves de SSH](https://help.github.com/en/articles/connecting-to-github-with-ssh) é o ideal em termos de praticidade e segurança.

## Criando e salvando arquivos no histórico de versões

Tudo que for criado ou alterado dentro de um repositório clonado será rastreado pelo git.

Para saber o status atual do rastreio, rode:

```
git status
```

> *Dica:* se a mensagem `fatal: not a git repository (or any of the parent directories): .git` aparecer, é porque você não está dentro do repositório clonado. No caso desse tutorial, você não rodou o `cd teste` para entrar no diretório do repositório clonado.

Depois de rodar `git status`, você deve ver algo como:

```
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
``` 

Isso indica que o git não tem mudanças para rastrear. Vamos criar alguma mudança. Rode o seguinte:

```
nano teste.txt
```

Escreva alguma coisa no arquivo, pressione <kbd>Ctrl+X</kbd> para salvar.

Em seguinda, rode `git status` novamente:

```
git status
```

Agora a mensagem será diferente:

```
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        teste.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Isso indica que o git achou o arquivo teste.txt, mas que ele não está sendo rastrado. Um arquivo não rastreado existe apenas na sua máquina, mas não no repositório online.

Você precisa que os arquivos estejam no repositório online para que seus colegas de equipe (ou você mesmo, em outra máquina) acessem o arquivo.

Vamos adicionar o arquivo `teste.txt` ao histório de versões (e, eventualmente, para o respositório). Primeiro dizemos ao git que queremos salvar o arquivo:

```
git add teste.txt
```

Depois de fazer isso, rode `git status` novamente:

```
git status
```

O git informará que agora está monitorando um novo arquivo (`teste.txt` no nosso caso):

```
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   teste.txt
```

Embora o arquivo esteja sendo monitorado, ele ainda não foi enviado salvo no histórico de versões. Salvar algo no histório de versão se chamada "commitar o arquivo".

Para fazer commit do arquivo, rode:

```
git commit -m "Mensagem"
```

> *Dica:* ao invés de `"Mensagem"`, use uma mensagem curta e descritiva do que esse commit faz. Por exemplo, algo como `"cria um arquivo para testes"`. Mensagens de commit são importantes porque elas ajudam outros desenvolvedores a entender o que está acontecendo com a base de códigos.

Depois de rodar o comando `git commit -m "...."`, você verá algo como:

```
[master 4b0aba7] Cria arquivo de testes
 1 file changed, 1 insertion(+)
 create mode 100644 teste.txt
```

Se mais de um arquivo foi commitado, ele aparecerá nessa lista.

## Enviando arquivos para o servidor/repositório online

Tudo que fizemos até agora alterou o histório de versão local, mas não o repositório online. Para enviarmos ao repositório online, usamos `git push`:

```
git push
```

Isso enviará todas as alterações feitas no seu computador (e commitadas) para o respositório online. Se outras pessoas estiverem trabalhando com você no projeto, você precisa periodicamente *baixar* as alterações que seus colegas estão fazendo.

Para baixar atualizações, rode:

```
git pull
```

O git verificará quais arquivos mudaram e baixará eles para você. O git é esperto o suficiente para juntar um mesmo arquivo que foi alterado por você e outro colegado ao mesmo tempo. O nome dessa operação é _merge_ (o git faz merge automático na maior parte dos casos)

## Resumo

Para resumir, o processo é o seguinte:

1. `git clone URL pasta`
2. `cd pasta`
3. Altera arquivos (quanto menos arquivos alterados por commit, melhor)
4. `git add arquivo` (ou `git add .` para adicionar tudo que foi alterado)
5. `git commit -m "mensagem legal"`
6. `git push`
7. `git pull`

Geralmente, depois de fazer o passo `5` acima, é recomendável rodar `git pull` (passo `7`) para atualizar seus arquivos locais com quaisquer alterações feitas no respositório online.

Repita os passos `4`, `5` e `6` toda vez que precisar alterar/criar algum arquivo, depois o passo `7` para enviá-lo para o repositório online.

## Comece a usar git

Pronto, é isso. Bem-vindo ao mundo real do desenvolvimento. No começo, trabalhar com git pode parecer trabalhoso (vários comandos para lembrar, etc), mas é uma ferramenta profissional essencial. Absolutamente __ninguém__ desenvolve software profissionalmente sem controle de versão, seja git ou outra solução.

Seu repositório do Github é o primeiro cartão de visitas que qualquer empresa olhará. Cuide bem dele!