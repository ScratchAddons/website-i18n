---
title: Criando um Addon
---
Software necessário: editor de texto, Chrome.  
Se possível, desabilite a extensão Scratch Addons que você baixou da loja antes de continuar para evitar problemas.

## Passo 1: Leia sobre [os básicos de um addon](addon-basics)
Leia aquele artigo para se familiarizar com a terminologia.

## Passo 2: Fork/clone o repositório
Ou baixe o código como ZIP, se quiser. Em outras palavras, só baixe o código fonte para o seu computador.

## Passo 3: Carregue a extensão no Chrome
*Nota: O Chrome é recomendado para desenvolver addons, mas se espera que os addons funcionem no Firefox também.*  
Agora que você tem a extensão baixada, vá para `chrome://extensions` e ative o "modo de desenvolvedor".  
Clique em "carregar sem compactação", então selecione a pasta onde o Scratch Addons está. Se você tiver problemas, certifique-se de que você está selecionando a pasta que contém o arquivo `manifest.json`.  
Pronto, você carregou a extensão! Ela deve se parecer com isso:  
![imagem](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Nota: você pode ignorar os "erros" sem problema. Eles são só avisos sobre uma chave não reconhecida no manifest que é necessária pro Firefox.

## Passo 4: Seu addon é sobre o quê?
Agora chegou a parte divertida!  
O que o seu addon vai fazer? Pense em um ID descritivo para o seu addon (sem espaços ou caracteres especiais, exceto hifens).  
Entendeu?

## Passo 5: Crie a pasta do seu addon
Usando um explorador de arquivos, vá para a pasta do Scratch Addons no seu computador. Abra a pasta `addons`.  
Então, crie uma nova pasta com o nome do ID do seu novo addon super épico.

## Passo 6: Adicione um manifest pro addon
O manifest do addon diz ao Scratch Addons como o seu addon funciona. Pra evitar dor de cabeça no futuro, tente deixar as informações todas certas desde o início.  
Nessa pasta que você criou, crie um arquivo `addon.json`.  
Essa é uma base que você pode usar para começar a produzir, lembre-se de mudá-la no futuro:
```json
{
  "name": "Aaaaaaaaaa my addon",
  "description": "Hello world!",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Para mais informações sobre o que você pode colocar nesse manifest, veja [este artigo](/docs/developing/the-addon-manifest-(addon.json)).


## Passo 7: Diga ao Scratch Addons qual o ID do seu addon
O Scratch Addons não consegue achar novas pastas sozinho, então você precisa adicionar o nome da pasta a um arquivo especial.  
Vá para `scratchAddonsFolder/addons/addons.json` e adicione o ID do seu addon à lista.

## Passo 8: Olá mundo
Por enquanto seu addon não faz nada, então é uma boa hora para checar se tudo que fizemos até agora funcionou.  
Vá para `chrome://extensions` e recarregue o Scratch Addons clicando no símbolo de recarregar em seu painel.
Agora, clique com o botão direito no ícone do Scratch Addons e clique em "opções".  
Seu addon vai aparecer na lista! Quando você achá-lo, ative-o, e mude quaisquer opções que você tiver.

## Passo 9: A parte legal, o código!
*Antes de continuar, leia o artigo da wiki linkado no passo 1.*

Agora chegou a melhor parte: crie seus próprios arquivos JS ou CSS!  
Dica: depois de mudar qualquer coisa no seu addon, lembre-se de recarregar a extensão do Scratch Addons assim como no passo 8.

Dependendo do que você quer que o seu addon faça, você deve ler essas páginas da wiki:
- [Scripts persistentes](/docs/develop/addon-types/persistent-scripts)
- [Userscripts](/docs/develop/addon-types/userscripts)
- [Userstyles](/docs/develop/addon-types/userstyles)

## Passo 10: Deixe seu addon customizável
Se você quiser, pode deixar o seu addon customizável!  
Usuários do seu addon poderão mudar configurações, digitar números, e mais!  
Para começar, veja [como declarar opções no manifest do addon](/docs/reference/addon-manifest/#settings-object).  
Então, vá para a [documentação do addon.settings](/docs/reference/addon-api/addon.settings) para aprender como acessar as opções do usuário através de userscripts e scripts persistentes.

## Passo 11: Antes de publicar o seu addon
Agora que o seu addon funciona, vamos checar se podemos adicioná-lo à biblioteca de addons.  
Cheque o manifest do seu addon para ver se está bom, [mais informações aqui](/docs/reference/addon-manifest). Preste atenção no nome, descrição e tags do seu addon. Lembre-se de deixar `"enabledByDefault"` marcado como `false` ou de só removê-lo.  
Veja se o seu addon não causa problemas em outros addons.  
Veja se o seu código é inteligível; é melhor ter comentários desnecessários do que nenhum.

## Passo 12: Mande um pull request!
Faça fork do repositório se já não fez isso, faça commit do seu novo addon e mande um PR!
Pode ser que peçamos que você faça mudanças, mas se o seu addon for minimamente aceitável, provavelmente vamos aceitá-lo.
