---
Livro: obsidian://open?vault=LEITURA&file=02%20Estudo%2FCDC%20-%20Web%20Design%20Responsivo.pdf
---
# PROBLEMA

Grande demanda dos usuários por utilzar aparelhos mobile para acessar a web -> importancia do desgin repsonsivo

# Qual a solução? 

A solução para que a web possa evoluir e os desenvolvedores possam atualizar seu know-how teórico e prático é:

- layout fluído 
- imagens flexíveis
- media-queries

# Maneiras de contornar

Tomemos como exemplo o Wikipédia que, atualmente, vai redirecioná-lo para a página http://en.m.wikipedia.org/ se o acesso for mobile. Chamamos isto de estratégia do <mark style="background: #FF5582A6;">“m ponto”</mark> (m.website.com). Eles não usam media queries e nem nada mais avançado para responsivar. Mas é responsivo? Ninguém sabe dizer ao certo, fica numa área cinza...

há ainda quem fale de uma outra técnica chamada <mark style="background: #FF5582A6;">RESS - Responsive design + Server Side components.</mark> Você serve a mesma URL, mesma página, mas ajusta no server-side algumas coisas sabendo qual browser é. Faz-se user-agent sniffing, que é menos preciso, mas ajuda em algumas coisas, como decidir se um link para ligação direta no celular deve ser exibido.

Um outro conceito um pouco diferente é o de <mark style="background: #FF5582A6;">One Web</mark>. Que devemos ter uma URL só pra tudo, um sistema só e servir mesmo conteúdo pra todo mundo. O Design Responsivo costuma ser uma forma de implementar One Web com usabilidade adequada pra todo mundo.

# OBJETIVO

Focaremos em Design Responsivo com One Web. Ou seja, exploraremos os exemplos e cenários de sites únicos se adaptando através de:

- Media Queries;
- CSS flexível;
- Recursos Flexíveis.