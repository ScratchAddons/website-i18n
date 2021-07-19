---
title: Básicos dos Addons
---

## O que exatamente é um addon?
Na verdade, um addon é nada mais que a combinação de pelo menos um desses tipos de arquivo: scripts persistentes, userscripts e userstyles. Se você precisar de mais de um desses, eles serão parte do mesmo addon, sob o mesmo nome. Por exemplo, o addon "Ferramentas de Desenvolvedor Scratch 3" tem um userscript que adiciona uma caixa de busca ao editor, e um userstyle que adiciona CSS à caixa.

## O que é um script persistente?
Um script persistente é código JavaScript que está sempre rodando em segundo plano, mesmo que o usuário não tenha nenhuma aba do Scratch aberta. Eles são úteis para, por exemplo, mandar notificações para o usuário sobre atualizações no Scratch. Scripts persistentes são parecidos com background scripts em extensões de navegador.

## O que é um userscript?
Um userscript é código JavaScript que roda junto com uma aba do Scratch. Diferente de scripts persistentes, você pode especificar em que páginas o userscript vai rodar, por exemplo, só em páginas de projetos. Userscripts são parecidos com content scripts em extensões de navegador, e se você já usou um administrador de userscripts, verá que esses são basicamente a mesma coisa.  
Userscripts são úteis para mudar o comportamento do site do Scratch, por exemplo, adicionar ou remover botões na barra superior.

## O que é um userstyle?
Um userstyle é parecido com um userscript; você também pode especificar padrões de URL para eles. Porém, userstyles injetam CSS ao invés de JavaScript. Eles costumam ser usados junto de userscripts para mudar a aparência de elementos adicionados por eles, mas eles também podem mudar o estilo de elementos nativos do Scratch. Nesse caso, o addon normalmente é chamado de "tema" (themes).

## Eu preciso mesmo criar um novo addon?
Você pode estar se perguntando se não é uma ideia melhor só mudar um addon que já existe ao invés de criar um novo.  
Se 2 addons compartilharem algumas dessas coisas, eles provavelmente podem ser combinados.
- Ambos precisam, ou não, de permissões que requerem interação do usuário (como notificações).
- Eles têm muito código idêntico.
- Um usuário comum esperaria que um addon só tivesse ambas as funções.
- Se eles causam interferência sendo addons separados.

Lembre-se que addons podem ser customizados pelo usuário - adicionar novas funções a um addon não precisa afetar usuários antigos do addon, a não ser que liguemos a função seja ativada por padrão.