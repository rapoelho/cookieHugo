# cookieHugo 🍪

O cookieHugo é um tema escuro e minimalista para o [Hugo](https://gohugo.io), usando a paleta de cores do Catppuccin Mocha e ele foi desenhado para ser adaptado e atender diversos propósitos, servindo tanto para um [Blog sobre Informática](https://rapoelho.com.br) ou mesmo um [Blog onde artes podem ser postadas](https://madebyromeo.com).

## ✨ Funcionalidades

- 🔍 **Busca interna com Pagefind:** Um sistema de pesquisa leve e que não exige Banco de Dados.
- 📦 **Tipos de Postagens:** Os cartões das postagens na tela inicial e em outras partes internas podem ser configurados. Notas podem ter uma borda de uma cor, Artigos podem ter capas. Você decide.
- **🏠 Capa da Página Inicial:** Também tem a opção de colocar uma mensagem de boas-vindas com links para páginas relevantes.

### 🔍 Busca Interna com Pagefind

O Pagefind é um sistema de busca criado especificamente para sites feitos em Geradores de Site Estático, como o Hugo. Ele faz isso sem precisar de um Banco de Dados, com o Índice dele sendo gerado depois de gerar o site.

#### 🛠️ Instalando e usando o Pagefind

Há três formas para instalar (e usar) o Pagefind: Pelo `npm`, pelo `pip` ou com o binário pré-compilado. 

**Pelo `npm`:** Para aqueles que já usam os pacotes do NodeJS, via `npm`, pode instalar (e usar) o Pagefind com esses comandos:

```bash
hugo --minify
npx pagefind --site "public"
```

**Pelo `pip`:** Para aqueles que usam o ambiente de desenvolvimento do Python, há a opção de instalar o Pagefind  com esse comando...

```bash
python3 -m pip install 'pagefind[extended]'
```

E depois de instalado, usar essa dupla de comandos:

```bash
hugo --minify
python3 -m pagefind --site "public"
```

**Usando o Binário:**  Para aqueles que querem instalar o Pagefind manualmente, tem a opção de [baixar o binário do Pagefind](https://github.com/pagefind/pagefind/releases). Basta baixar de acordo com o Sistema Operacional que você utiliza, e executar ele por linha de comando.

```bash
hugo --minify
./pagefind --site "public"
```

E assim, o Pagefind irá gerar os arquivos necessários para o uso dele no site.


### 📦 Tipos de Postagens

Às vezes queremos postar algumas coisas e fazem com que as postagens pareçam ser um pouco diferentes entre si. E é aqui que esse recurso entra. Para modificar como esse recurso irá se comportar, copie o arquivo `postTypes.yml` na pasta `data` na pasta Raiz do seu projeto Hugo, e esse arquivo se parece assim:

```yaml
types:
  - id: posts
    icon: 📰
    label: "Artigo Completo"
    cover: true
    #~ border_color: "#f3a072"
    #~ border_style: "dashed"
    #~ border_width: "2px"
  
  - id: notas
    icon: 🗒️
    label: "Nota Rápida"
    cover: false
    border_color: "#f3a072"
    border_style: "dashed"
    border_width: "2px"
```

E indo para cada uma das opções:

- **`id`:** Aqui fica o nome da pasta onde se localizam as postagens que pertencem aquele tipo;
- **`icon`:** Esse tema utiliza Emojis para os ícones que ficam ao lado do título da postagem indicando o tipo dela;
- **`label`:** Essa opção é o Rótulo do Ícone que irá aparecer ao passar o mouse por cima do ícone;
- **`cover`:** Aqui é configurado se a Capa do Post irá aparecer ou não nas listagens de posts.
- **`border_color`:** Aqui se configura a cor da Borda que irá aparecer ao redor das postagens daquele tipo;
- **`border_style`:** Aqui se aplica o estilo da Borda que será usada ao redor das postagens daquele tipo;
- **`border_width`:** E por fim, aqui se aplica a grossura da borda que será usada ao redor das postagens daquele tipo.

### 🏠 Capa da Página Inicial

Outra funcionalidade desse tema é a possibilidade de ativar uma Capa na Página Inicial, em que se pode colocar algum texto sobre o Blog e alguns links. Isso é alimentado pelo arquivo `homeCover.yml` e ele é assim:

```yml
title: Hewyo!
subtitle: Esse é o cookieHugo, um tema aconchegante baseado na paleta do Catppuccin Mocha
background: 

links:
  - title: Exemplo de Blog com o Tema
    link: https://rapoelho.com.br
  - title: Todos os Posts
    link: /archives
```

### 📬 Automação para o Make.com vis  RSS

Outra funcionalidade desse tema é um RSS já preparado para Redes Sociais, para ser usado em automações no Make.com e já está ativado por padrão, sendo gerado um arquivo `social.xml` na raiz do site.  E há suporte para quatro tipos de postagens:

**🗒️ Apenas Texto:** Esse é o modo padrão desse recurso. Os únicos campos a serem preenchidos são o `longCaption` e `shortCaption`. As opções do Front Matter ficariam assim:

```yaml
social:
  post: true
  
  longCaption: "Eu tinha automatizado as postagens do made by romeo, então decidi fazer o mesmo com a toca do rapoelho.\n\nCom isso, tive a oportunidade de simplificar e gostei bastante desse resultado. Acho que agora ficou bem mais simples de entender como isso funciona."
  shortCaption: 
```

E já no RSS, esse é o resultado:

```xml
<item>
	<title>Postando nas Redes Sociais com um Blog</title>
	<link>http://localhost:1313/posts/hugo-social/</link>
	<post>true</post>
	<longCaption>
	Eu tinha automatizado as postagens do made by romeo, então decidi fazer o mesmo com a toca do rapoelho. Com isso, tive a oportunidade de simplificar e gostei bastante desse resultado. Acho que agora ficou bem mais simples de entender como isso funciona.
	</longCaption>
	<media>false</media>
	<postImage>false</postImage>
	<postAlbum>false</postAlbum>
	<postVideo>false</postVideo>
</item>
```

**🖼️ Imagem Única:** Nesse modo, é configurada uma única imagem. Os campos a serem configurados são o `longCaption` e `shortCaption` para o texto, o `postImage` para ativar a postagem da imagem e o `image` para definir a imagem a ser postada.  As opções do Front Matter ficariam assim:

```yaml
social:
  post: true
  media: true
   
  postImage: true
  image: images/01-nippy-power-daemon.webp
  
  longCaption: "Mais um tijolinho que estou construindo no Nippybox: Um Gerenciador de Energia. Ainda está bem básico, mas está funcional."
  shortCaption: 
```

E já no RSS, esse é o resultado:

```xml
<item>
	<title>Um Daemon de Energia para o Nippybox</title>
	<link>http://localhost:1313/notas/n24-bateria/</link>
	<post>true</post>
	<longCaption>
	Mais um tijolinho que estou construindo no Nippybox: Um Gerenciador de Energia. Ainda está bem básico, mas está funcional.
	</longCaption>
	<media>true</media>
	<postImage>true</postImage>
	<image>
	http://localhost:1313/notas/n24-bateria/images/01-nippy-power-daemon.webp
	</image>
	<postAlbum>false</postAlbum>
	<postVideo>false</postVideo>
</item>
```

**📹 Vídeo:** Esse é um modo bem parecido com  anterior, mas é específico para vídeos. Os campos a serem configurados são o `longCaption` e `shortCaption` para o texto, o `postVideo` para ativar a postagem do Vídeo e o `video` para definir o vídeo a ser postado.  As opções do Front Matter ficariam assim:

```yaml
social:
  post: true
  media: true
    
  postVideo: true
  video: media/01-colorizer.mp4
  
  longCaption: "Havia mencionando anteriormente que eu havia refeito o nippy-colorizer. \n\nEsse foi o resultado: Ele foi refeito em Python e está muito mais rápido, e ainda aplica o tema GTK numa paleta próxima ao tema. \n\nAté tive uma ajuda do Gemini para isso, mas pretendo estudar o código e refazer o nippy-colorizer com as minhas próprias mãos."
  shortCaption: 
```

E já no RSS, esse é o resultado:

```xml
<item>
	<title>Novo nippy-colorizer para o Openbox</title>
	<link>http://localhost:1313/notas/n21-colorizer/</link>
	<post>true</post>
	<longCaption>
	Havia mencionando anteriormente que eu havia refeito o nippy-colorizer. Esse foi o resultado: Ele foi refeito em Python e está muito mais rápido, e ainda aplica o tema GTK numa paleta próxima ao tema. Até tive uma ajuda do Gemini para isso, mas pretendo estudar o código e refazer o nippy-colorizer com as minhas próprias mãos.
	</longCaption>
	<media>true</media>
	<postImage>false</postImage>
	<postAlbum>false</postAlbum>
	<postVideo>true</postVideo>
	<video>
	http://localhost:1313/notas/n21-colorizer/media/01-colorizer.mp4
	</video>
</item>
```

**📕 Galeria**: E por fim, o modo mais diferente dos três de mídia. Aqui, é configurada a Galeria para a postagem de mais de uma imagem, e os campos a serem configurados são o `longCaption` e `shortCaption` para o texto, o `postAlbum` para ativar a postagem do álbum de imagens e o `albumImages` para definir as imagens a serem postadas.  As opções do Front Matter ficariam assim:

```yaml
social:
  post: true
  media: true
  
  postAlbum: true
  
  albumImages:
    - images/01-fastfetch-win.webp
    - images/02-fastfetch-lnx.webp
    - images/03-fastfetch-lnx.webp   
  
  longCaption: "E esses são os Sistemas Operacionais em meus Notebooks: Windows 10 e Void Linux no meu velho Inspiron 5558 e o Void Linux no meu Thinkpad L390. \n\nE realmente, configurar a Linha de Comando do Windows é um porre."
  shortCaption: 
```

E já no RSS, esse é o resultado:

```xml
<item>
	<title>Dois Notebooks, Três Sistemas Operacionais</title>
	<link>http://localhost:1313/notas/n23-linux-win/</link>
	<post>true</post>
	<longCaption>
	E esses são os Sistemas Operacionais em meus Notebooks: Windows 10 e Void Linux no meu velho Inspiron 5558 e o Void Linux no meu Thinkpad L390. E realmente, configurar a Linha de Comando do Windows é um porre.
	</longCaption>
	<media>true</media>
	<postImage>false</postImage>
	<postAlbum/>
	<album>
	http://localhost:1313/notas/n23-linux-win/images/01-fastfetch-win.webp , http://localhost:1313/notas/n23-linux-win/images/02-fastfetch-lnx.webp , http://localhost:1313/notas/n23-linux-win/images/03-fastfetch-lnx.webp ,
	</album>
	<postVideo>false</postVideo>
</item>
```

#### ✅ Todas as Opções no Front matter

Essas são todas as opções que podem ser usadas no Front Matter das Postagens para gerar o RSS das Redes Sociais:

```yaml
social:
  post: true

  longCaption: " "
  shortCaption: " "
  
  postImage: false
  image: 
  
  postVideo: false
  video: 
  
  postAlbum: true
  albumImages:
    - 
    - 
    - 
```

E descrevendo cada uma dessas opções:

- **`post`:** Essa é a opção que define se o conteúdo deve ser postado ou não. O valor padrão é `false`.
- **`longCaption`:** Aqui é o campo onde se coloca legendas mais longas para as Redes Sociais que permitem isso, como o Telegram e o Facebook.
- **`shortCaption`:** Esse é o campo onde se coloca as legendas mais curtas para as Redes Sociais que tem uma restrição de Caracteres, como o Twitter/X e o Bluesky.
- **`postImage`:** Essa é a opção que define se será postada alguma imagem junto com o post. O valor padrão é `false`.
- **`image`:** Aqui é onde se define a imagem que será postada. Apenas isso.
- **`postVideo`:** Essa é a opção que define se será postado algum vídeo junto com o post. O valor padrão é `false`.
- **`video`:** Aqui é onde se define o vídeo que será postado.
- **`postAlbum`:** Essa é a opção que define se será postada múltiplas imagens em um post.
- **`albumImages`:** Aqui é onde se define a lista das imagens a serem postadas.

## 🚀 Instalando o Tema

Dentro da raiz do seu projeto Hugo, execute o seguinte comando para adicionar o tema como um submódulo Git:

```bash
git submodule add https://github.com/rapoelho/cookieHugo themes/cookieHugo
```

Em seguida, adicione o nome do tema no seu arquivo principal de configuração (`hugo.yaml`):

```yaml
theme: "cookieHugo"
```

## ⚙️ Configuração Recomendada

Para tirar o máximo proveito do controle de SEO, da busca interna e das datas localizadas do tema, configure o seu arquivo **`hugo.yaml`** seguindo este modelo de referência:

```
title: "Seu Nome ou Nome do Site"
baseURL: "https://seusite.com"
theme: "cookieHugo"

# Configurações de Idioma
languageCode: "pt-br"
defaultContentLanguage: pt
defaultContentLanguageInSubdir: false

# Ativação do robots.txt
enableRobotsTXT: true 

# Parâmetros Customizados do Tema
params:
  pagination:
    pagerSize: 10 # Configuração da Paginação do tema
    
  posts: ["posts", "notas"] # Pastas onde estão as postagens do Blog
  
  description: "Um tema aconchegante que usa o Catppuccin Mocha." # Descrição para SEO
  footer: "| Hewyo! " # Texto personalizado no Rodapé
  
# Configuração das Fontes do Blog
  fonts: 
    main: "Albert Sans"  # Fonte padrão do Blog
    title: "Albert Sans" # Fonte para títulos do Blog
    monospace: "JetBrains Mono"  # Fonte Monoespaçada

# Configurações de SEO  
  seo: 
    # Configurações de Indexação
    index:
      taxonomies: false # Ativar a Indexação das Taxonomias. Padrão: false
      paginated: false # Ativar a Indexação da Paginação. Padrão: false
    
    # Configurações do OpenGraph
    opengraph:
      defaultImage: "" # Imagem padrão do Opengraph. Padrão: /images/site/share.webp
    social:
      twitterUser: "" # Usuário do Twitter/X, para uso nos Card do Twitter/X.
  
# Configurações de Customização
  customization: 
    homeCover: false # Ativar a Capa da Home. Padrão: false
    logo: "" # Configurar o Logo do site. Padrão: /images/site/logo.webp

# Configurações dos Favicons
  favicons:
    ico: ""
    png16: ""
    png32: ""
    png96: ""
    apple: ""
    android192: ""
    android512: ""

# Configurações de Analytics    
  analytics:
    # Para o Plausible
    plausible:
      scriptUrl: ""
      domain: ""
    # Para o Umami
    umami:
      scriptUrl: ""
      websiteId: ""
    
services:    
  # Para o Google Analytics
  googleAnalytics:
    id: ""

# Configuração dos Menus
menu:
  # Menu das Redes Sociais
  icons:
    - identifier: "github"
      name: "GitHub"
      url: "https://github.com/rapoelho"
      weight: 10

# Configuração das Saídas
outputs:
  home:
    - HTML
    - RSS

```

## 📝 Licença e Créditos

Este projeto está licenciado sob a licença **GNU Affero General Public License v3.0 (AGPLv3)**. Consulte o arquivo `LICENSE` para obter mais detalhes.

O **cookieHugo** foi desenvolvido por **Rapoelho** e utiliza trechos de código e inspirações lógicas do tema [Ficurinia](https://github.com), licenciado sob a AGPLv3. Um agradecimento especial ao autor original pela contribuição ao ecossistema do Hugo.

## 📑 Changelog

- **11-Out-2026:** Adicionado o RSS Social
- **27-Set-2026:** Adicionado Shortcode de Vídeo
- **07-Jun-2026:** Lançamento Inicial
