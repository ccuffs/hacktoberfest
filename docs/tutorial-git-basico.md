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

É muito importante que seus dados de desenvolvedor (nome, e-mail, etc) estejam corretamente informados ao git. Essas informações aparecerão no histórico de versões do seu projeto.

Para alterar o seu nome, rode o seguinte (troque `Fulano da Silva` pelo seu nome):

```
git config user.name "Fulano da Silva"
```

Para alterar o seu e-mail, rode o seguinte (troque `fulano@silva.com` pelo seu e-mail):

```
git config user.email "fulano@silva.com"
```

Para ver quais as informações que o git tem gravadas, rode:

```
git config --list
```