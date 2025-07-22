---
Praticar: https://codepen.io/oliveryeahh/pen/PwPqBeB
---
Veremos como converter um layout fixo em layout fluído. Primeiro, devemos nos ater a um dos mais importantes detalhes técnicos quando o assunto é web design responsivo: a meta tag viewport.

O termo meta tag é, na verdade, formado por 2 palavrinhas que se juntam para dar seu significado. 

- Meta é um prefixo grego que significa algo como “após”, “que ultrapassa”, “que engloba”. Refere-se à “coisa sobre a própria coisa” ou, em outras palavras, dados sobre dados, informação sobre a informação.
- Tag é uma palavra do inglês que significa “etiqueta” ou “rótulo”.

Juntando, temos meta tag, que são tags que descrevem o documento web a qual pertencem (“informação sobre a informação”); as meta tags são para descrever informações sobre sites e páginas que as contém; 

As metatags são colocadas como elementos-filho de head no HTML. Sua sintaxe obedece à seguinte convenção:

```html
	<meta name="nome-da-meta" content="conteudo-da-meta">
```

# O que é a meta tag viewport

Os browsers mobile tentam exibir páginas web feitas somente para desktop ajustando, automaticamente, o zoom do display, e isso pode ser problemático para os sites que já foram planejados/otimizados para telas pequenas 

Felizmente, existe uma meta tag para contornar essa característica dos navegadores. É a meta tag viewport. Assim como qualquer outra meta tag, ela possui o formato:

```html
<meta name="viewport" content="">
```

Sendo que, em content, é possível especificar uma diversidade de parâmetros e valores conforme o tipo de visualização que se configurar às páginas. Se preferir, pense que com a meta tag viewport, é possível apresentar “resoluções personalizadas” aos visitantes para determinados devices. Os principais e mais usados parâmetros de content são:

- width: define a largura da viewport;
- height: define a altura da viewport;
- initial-scale: define a escala inicial (zoom) inicial da viewport.


# Vamos ver na prática

| Imagem                                       | Explicação                                                                                                                                                                                                                                                                            |
| -------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![[Pasted image 20250715132951.png \| 300]]  | Veja uma imagem de 320x356px, apresentada num iPhone, renderizada usando as configurações default de viewport.                                                                                                                                                                        |
| ![[Pasted image 20250715133602.png \| 300 ]] | Agora, a página com o zoom na viewport sendo o mesmo do da própria imagem.                                                                                                                                                                                                            |
| ![[Pasted image 20250715133725.png \| 300]]  | No entanto, como se trata de configurações que podem ser escolhidas conforme a necessidade do projeto, o zoom na viewport pode ser maior ou menor do que a área visível. <br><br>Se o zoom é maior do que a área visível, então será possível deslizar a tela para ver mais da página |
| ![[Pasted image 20250715134110.png \| 300]]  | E, como citado, também é possível definir um zoom menor para a viewport.                                                                                                                                                                                                              |
| ![[Pasted image 20250715134148.png \| 300]]  | Nos dispositivos móveis, a pessoa também pode fazer zoom in e zoom out usando gestos. Quando isso acontece, ela não altera o tamanho da viewport; altera sua escala! Consequentemente, os gestos de pan e zoom não alteram o layout da página.                                        |

# A configuração ideal

Até agora vimos valores fixos setados no viewport, mas levando em consideração a quantidade absurda de dispositivos com diferentes tamanhos, proporções e resoluções, seria extremamente difícil fazer a adaptação manual para cada um. Por isso, existe a seguinte opção:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Também é interessante que, assim que a página renderize, não haja alterações na escala inicial. Por isso, juntamente com width=device-width da meta tag viewport, é bom usar a initial-scale em 1

Isso indica ao navegador que o width da meta tag viewport é o tamanho da largura do dispositivo!

---
Este é o momento para praticar. O link para um exercício com design flexível está no início deste texto.