---
title: Userstyles
description: Userstyles te deixam injetar CSS no site do Scratch - útil para mudar a aparência de botões que você adiciona com userscripts, ou para customizar elementos nativos do Scratch.
---

Userstyles te deixam injetar CSS no site do Scratch - útil para mudar a aparência de botões que você adiciona com userscripts, ou para customizar elementos nativos do Scratch.

## Como eu adiciono um userstyle?
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças no seu addon.**
Vá para o manifest do seu addon (addon.json) e adicione uma propriedade chamada `"userstyles"`.  
Essa propriedade deve ser uma array (matriz/lista).  
Cada item da array deve ter as seguintes propriedades: `"url"` e `"matches"`.  
`"url"` deve ser um URL relativo que aponta a um arquivo CSS.  
`"matches"` deve ser uma array de URLs nos quais você quer executar o userscript. Você pode usar asteriscos.
Exemplo de manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userstyles": [
    {
      "url": "userstyle.css",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userstyle.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Depurando userstyles
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças no seu addon.**  
Se o seu userstyle não estiver funcionando, veja se ele está ativado.  
Se você ainda estiver com problemas, por favor crie um issue nesse repositório.
