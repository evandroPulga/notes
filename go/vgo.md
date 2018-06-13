# vgo

É uma versão do cli go com suporte a versionamento. Os comandos do cli go foram mantidos, porém, foram alterados para usar o sistema de versionamento. O vgo utiliza um arquivo go.mod na raiz do projeto, esse arquivo define o nome do módulo e as dependências. O nome do módulo será utilizado para importar o módulo em outros projetos.

Um módulo é um conjunto de pacotes versionados como uma unidade, pode ser um software, uma biblioteca etc.

# Comandos básicos
*  `go get -u golang.org/x/vgo` instala o vgo.
*  `vgo build` cria ou atualiza o arquivo de dependências com as dependências do projeto e faz o build normal do comando go.
*  `vgo list -m -u` lista as dependências e versões.
*  `vgo get <package>` atualiza uma dependência e altera a versão requerida no arquivo de dependências.
*  `vgo test all` testa os pacotes incluíndo as dependências, recomendado executar sempre que atualizar uma dependência.
*  `vgo get -u` atualiza todas as dependências requeridas pelo build.

# versionamento

Vgo sempre vai preferir uma versão tageada semântica (v0.0.1 > v0.0.0 wildcard tag).

Major versions devem ser definidas na declaração de módulo no arquivo go.mod, seguindo o padrão */v<ver. num.>. Ex:

v1: `module "my/thing"`

v2: `module "my/thing/v2"`

Imports dentro de uma versão devem ser escritos com base no versionamento. Ex:

v1: `import "my/thing/foo"`

v2: `import "my/thing/v2/foo"`
