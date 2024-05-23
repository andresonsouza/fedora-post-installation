# Guia de pós-instalação Fedora 40 workstation, para desenvolvimento web e produção audiovisual

Olá! Andreson Souza aqui!

Quero compartilhar com vocês aqui os passos que utilizo para configurar o sistema para minhas necessidades, a distro em questão aqui neste artigo é a Fedora 40.
 
## 1 Utilitários do Sistema <br/>
1.1 Atualização do sistema <br/>
1.2 Atualização do idioma do sistema para PT-BR <br/>
1.3 Editor de textos Vim <br/>
1.4 Instalação e configuração do ZSH e [oh my zsh](https://ohmyz.sh/)

## 2 Ferramentas para Desenvolvimento Web
2.1 Instalação do VsCode <br/>
2.2 asdf - O gerenciador de múltiplas versões de linguagens <br/>
2.3 Instalação do nodejs usando asdf <br/>
2.4. Instale o gerenciador de pacotes yarn <br/>

## 3 Ferramentas para Produção Audiovisual

### 1 Utilitários do Sistema
Aqui vamos instalar ferramentas libs, codecs e ferramentas que são requisitos para funcionamento de vários softwares em geral

**1.1 Atualização do sistema**
Primeiro passo é atualizarmos o sistema para não termos nenhum problema durante a instalação e configuração dos apps, bibliotecas e afins.

```bash
sudo dnf update
```

**1.3 Editor de textos Vim**

O Vim é um editor de texto altamente configurável e poderoso, projetado para facilitar a edição eficiente de texto. Ele é amplamente utilizado em sistemas Unix e Unix-like, como Linux, e também está disponível para outros sistemas operacionais.

A instalação pode ser feita com o comando abaixo.

```bash
sudo dnf vim
```

**1.4 Instalação e configuração do ZSH e [oh my zsh](https://ohmyz.sh/)**

**O que é o ZSH**

O Zsh, ou Z Shell, é um interpretador de linha de comando (shell) para sistemas Unix-like, como Linux e macOS. Ele é uma alternativa ao shell mais comumente encontrado em sistemas Unix, o Bash (Bourne Again Shell), mas oferece uma série de recursos adicionais e aprimoramentos em comparação com o Bash e outros shells.

**Instalação do ZSH**

```bash
sudo dnf install zsh
```

**Tornar o ZSH SHELL padrão**
Abra o arquivo passwd usando o comando abaixo.

```bash
sudo nano /etc/passwd
```

Em seguida edite a linha do seu usuário. O conteúdo da linha é algo parecido como mostrado abaixo:

```bash
seu_usuario:x:1000:1000:Seu Nome:/home/seu_usuario:/bin/bash
```

Basta substituir o bash ao final da linha por zsh ficando assim:
```bash
seu_usuario:x:1000:1000:Seu Nome:/home/seu_usuario:/bin/zsh
```

**oh-my-zsh**

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**Alterando o tema para Agnoster**

Abra o arquivo .zshrc e edite a linha ZSH_THEME="robbyrussell". No lugar de "robbyrusell" coloque o nome do tema desejado, no meu caso o agnoster ficando assim:

ZSH_THEME="agnoster"

**Instalação de alguns Plugins**

## 2 Ferramentas para Desenvolvimento Web

**Instalação do VSCode**

Seguindo a [codumentação oficial](https://code.visualstudio.com/docs/setup/linux) podemos executar os comando abaixo para fazer a instalação.

Primeiro adicionamos o repositório
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
```

Em seguida verificamos se existem atualizações e instalamos o app.

```bash
dnf check-update
sudo dnf install code # or code-insiders
```

**2.2 [asdf](https://asdf-vm.com/) - O gerenciador de múltiplas versões de linguagens**

O gerenciador de linguagens ASDF (Another System Definition Facility) é uma ferramenta utilizada principalmente por desenvolvedores de software para gerenciar múltiplas versões de linguagens de programação e suas dependências em um sistema. Ele fornece uma maneira conveniente de instalar, atualizar e alternar entre diferentes versões de linguagens de programação, como Ruby, Node.js, Python, entre outras. 
É uma ferramenta poderosa que simplifica o gerenciamento de versões de linguagens de programação e suas dependências, contribuindo para um desenvolvimento mais organizado e eficiente de software.

**Download e configuração do  asdf**

```bash
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.0
```
Caso você esteja usando o Bash como Shell padrão, adicione a seguinte linha ao final do arquivo ~/.bashrc, se o shell for zsh adicione o arquivo ~/.zshrc.

```bash
. "$HOME/.asdf/asdf.sh"
```

Para configurar o auto-complete no shell bashh adicione a seguinte linha também ao ~/.bashrc.

```bash
. "$HOME/.asdf/completions/asdf.bash"
```

Caso o shell seja ZSH:

```bash
# append completions to fpath
fpath=(${ASDF_DIR}/completions $fpath)
# initialise completions with ZSH's compinit
autoload -Uz compinit && compinit
```
**2.3. Instalação do nodejs usando asdf**

Adicione o plugin com o comando abaixo.

```bash
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
```

Instale o nodejs na versão desejada, no meu caso vou instalar versão LTS do momento da criação desse tutotial.

```bash
asdf install nodejs v20.13.1
```

Torne a versão instalada anteriormente global utilizando o comando abaixo.

```bash
asdf global nodejs v20.13.1
```

**2.4 Instale o gerenciador de pacotes yarn**

O Yarn é um gerenciador de pacotes para JavaScript, criado pelo Facebook em colaboração com outras empresas como Google, Exponent e Tilde. Ele foi desenvolvido para ser uma alternativa ao npm (Node Package Manager), que é o gerenciador de pacotes padrão para o ecossistema Node.js.

**2.5 Instalação do Angular CLI**

O Angular CLI (Command Line Interface) é uma ferramenta de linha de comando oficial fornecida pelo time do Angular para facilitar o desenvolvimento de aplicativos Angular. Ele é projetado para automatizar tarefas comuns, como a criação de novos componentes, serviços, módulos, entre outros, além de fornecer um ambiente de desenvolvimento otimizado.

```bash
npm install -g @angular/cli
```

**2.6 Instalação do Typescript**

TypeScript é um superconjunto tipado de JavaScript que compila para JavaScript simples. Em outras palavras, o TypeScript adiciona tipagem estática opcional, classes, interfaces e outros recursos de orientação a objetos ao JavaScript. Desenvolvido e mantido pela Microsoft, o TypeScript visa melhorar a escalabilidade e a manutenibilidade do código JavaScript, especialmente em grandes projetos e equipes de desenvolvimento.

```bash
npm install -g typescript
```

