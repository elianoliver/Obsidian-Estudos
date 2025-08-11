A **MediaStream API** é uma interface do JavaScript que permite capturar áudio e vídeo de dispositivos locais, como a webcam ou o microfone do usuário. Diferente de simplesmente reproduzir áudio ou vídeo (como vimos com a HTMLMediaElement API), essa API é usada para **gravar** ou **transmitir** mídia diretamente do hardware do usuário, como em chamadas de vídeo, gravações de áudio ou streaming ao vivo.

Pense na MediaStream API como uma "ponte" que conecta o hardware do usuário (webcam, microfone) ao seu código JavaScript, permitindo que você use os dados de áudio e vídeo capturados em sua aplicação.

## **Como criar um MediaStream?**

Para capturar áudio ou vídeo, você precisa criar um objeto **MediaStream**, que representa o fluxo de mídia (stream) vindo do dispositivo. Embora seja possível criar um MediaStream com o construtor (`new MediaStream()`), isso não o conecta ao hardware do usuário. Em vez disso, você usa o método **`getUserMedia()`**, disponível no objeto `navigator.mediaDevices`.

O método `getUserMedia()` é o ponto de partida para acessar a webcam ou o microfone. Ele:

1. Pede permissão ao usuário para acessar o dispositivo (o navegador mostra um pop-up pedindo autorização).
   
2. Retorna um objeto **MediaStream** contendo os dados de áudio e/ou vídeo, se o usuário permitir.

## **O que é o objeto de constraints?**

O método `getUserMedia()` aceita um **objeto de constraints** (restrições) como argumento. Esse objeto define que tipo de mídia você quer capturar (áudio, vídeo ou ambos) e permite configurar detalhes, como a resolução do vídeo ou a qualidade do áudio.

O objeto de constraints tem duas propriedades principais:

- **audio**: Define se você quer capturar áudio. Pode ser:
  - `true` (captura áudio do microfone).
  - `false` (não captura áudio).
  - Um objeto com configurações específicas (como qualidade ou dispositivo específico).
    
- **video**: Define se você quer capturar vídeo. Pode ser:
  - `true` (captura vídeo da webcam).
  - `false` (não captura vídeo).
  - Um objeto com configurações específicas, como resolução.

Exemplo de constraints com configurações de resolução:
```javascript
const constraints = {
  audio: true, // Captura áudio
  video: {
    width: { min: 1280, ideal: 1920, max: 3840 }, // Largura do vídeo
    height: { min: 720, ideal: 1080, max: 2160 }  // Altura do vídeo
  }
};
```

Nesse exemplo:
- **min**: Resolução mínima aceitável (1280x720).
- **ideal**: Resolução preferida (1920x1080, ou Full HD).
- **max**: Resolução máxima permitida (3840x2160, ou 4K).
O navegador tentará fornecer um stream com a resolução mais próxima do valor `ideal`, respeitando os limites de `min` e `max`.

## **Como usar o getUserMedia()?**

O método `getUserMedia()` retorna uma **Promise**, o que significa que você precisa usar uma função de callback ou a sintaxe `async/await` para lidar com o resultado. Quando o usuário concede permissão, você recebe um objeto **MediaStream** que pode ser usado para exibir o vídeo, gravar áudio ou processar os dados de outras formas.

Exemplo prático para exibir o feed da webcam em um elemento `<video>`:
```javascript
async function startVideo() {
  try {
    // Solicita acesso à webcam
    const stream = await navigator.mediaDevices.getUserMedia({ video: true });
    
    // Associa o stream ao elemento <video>
    const video = document.querySelector('video');
    video.srcObject = stream;
    
    // Inicia a reprodução do vídeo
    await video.play();
  } catch (error) {
    console.error('Erro ao acessar a webcam:', error);
  }
}

// Chama a função para iniciar o vídeo
startVideo();
```

Nesse exemplo:
1. O método `getUserMedia({ video: true })` solicita acesso à webcam.
2. O objeto `stream` (MediaStream) contém o feed de vídeo.
3. O stream é associado ao elemento `<video>` usando a propriedade `srcObject`.
4. O método `play()` inicia a exibição do vídeo.

HTML correspondente:
```html
<video autoplay></video>
```

> **Nota**: O atributo `autoplay` no elemento `<video>` pode ser usado para iniciar a reprodução automaticamente, mas o método `play()` é necessário em alguns casos para garantir compatibilidade.

## **O que você pode fazer com o MediaStream?**

Depois de obter o objeto **MediaStream**, você pode:

- **Exibir o feed ao vivo**: Como no exemplo acima, associando o stream a um elemento `<video>`.
  
- **Gravar a mídia**: Usar a API `MediaRecorder` para gravar o stream como um arquivo.
  
- **Transmitir**: Enviar o stream para outros usuários em tempo real (como em uma chamada de vídeo).
  
- **Processar os dados**: Analisar o áudio ou vídeo com outras APIs, como para detecção de rosto ou efeitos visuais.

## **Limitações mencionadas**

- **Permissão do usuário**: O acesso à webcam ou microfone sempre requer autorização explícita do usuário, o que garante privacidade.
  
- **Sem captura de tela**: A MediaStream API não suporta captura de tela (como gravar a tela do computador). Para isso, existe outra API chamada **Display Capture API**, que será abordada em outra aula.
  
- **Promises**: Como `getUserMedia()` retorna uma Promise, você precisa lidar com operações assíncronas, usando `try/catch` com `async/await` ou `.then()`.

## **Exemplo completo**

Aqui está um exemplo mais detalhado que captura vídeo e áudio e exibe na página:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Captura de Webcam</title>
</head>
<body>
  <video id="webcam" autoplay></video>
  <button onclick="startCapture()">Iniciar Captura</button>
  <button onclick="stopCapture()">Parar Captura</button>

  <script>
    let stream = null;

    async function startCapture() {
      try {
        // Solicita vídeo e áudio com constraints
        stream = await navigator.mediaDevices.getUserMedia({
          video: { width: { ideal: 1280 }, height: { ideal: 720 } },
          audio: true
        });

        // Associa o stream ao elemento <video>
        const video = document.getElementById('webcam');
        video.srcObject = stream;
        await video.play();
        console.log('Captura iniciada!');
      } catch (error) {
        console.error('Erro ao acessar a mídia:', error);
      }
    }

    function stopCapture() {
      if (stream) {
        // Para todas as trilhas do stream
        stream.getTracks().forEach(track => track.stop());
        document.getElementById('webcam').srcObject = null;
        console.log('Captura parada!');
      }
    }
  </script>
</body>
</html>
```

Nesse exemplo:
- O botão "Iniciar Captura" solicita acesso à webcam e microfone com resolução ideal de 1280x720.
- O botão "Parar Captura" encerra o stream, liberando o acesso ao hardware.
- O vídeo é exibido em um elemento `<video>` com `autoplay`.

## **Resumo visual**

Pense na MediaStream API como uma "câmera virtual" que conecta a webcam ou microfone ao seu código. Para usá-la:

1. **Acesse o hardware** com `navigator.mediaDevices.getUserMedia(constraints)`.
   
2. **Configure constraints** para definir o tipo de mídia (áudio, vídeo) e detalhes como resolução.
   
3. **Use o MediaStream** para exibir, gravar ou processar os dados.
   
4. **Lide com Promises** para gerenciar a natureza assíncrona do método.

É como ligar uma câmera de segurança: você define como quer que ela grave (resolução, áudio, etc.), pede permissão para usá-la e, depois, usa o vídeo ao vivo como quiser.
