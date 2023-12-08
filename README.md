Para criar um bot do WhatsApp com conexão por código QR, podemos usar HTML e Node.js. Aqui está um guia passo a passo sobre como conseguir isso:

1°// Instale as dependências necessárias:

-Node.js: Baixe e instale o Node.js do site oficial.
-whatsapp-web.jspacote: Abra seu terminal e execute o seguinte comando para instalar o pacote:
` 

## NPM
```
npm install whatsapp-web.js
```
2°// Crie um novo arquivo HTML:

-Abra seu editor de texto favorito e crie um novo arquivo HTML, por exemplo, index.html.
-Adicione a estrutura e os elementos HTML necessários para criar uma interface de usuário para seu bot.

3°// Configure o servidor Node.js:

Crie um novo arquivo JavaScript, por exemplo, server.js.
Importe os módulos necessários:

EM CASO DE USO DA BAILEYS TROQUE NA LINHA 4 O 'whathsapp-web.js' por 'adiwajshing/baileys'

## SERVER JS
```
const express = require('express');
const app = express();
const { Client } = require('whatsapp-web.js');
const qrcode = require('qrcode');
```

4°// Gere um código QR:

-Use o módulo qr core para gerar um código QR que o usuário pode escanear para conectar sua conta do WhatsApp.
-Adicione o seguinte código ao seu server.js arquivo:

## GET QR
```
app.get('/qr', (req, res) => {
  qrcode.toDataURL('https://web.whatsapp.com')
    .then(url => {
      res.send(`<img src="${url}" alt="QR Code" />`);
    })
    .catch(err => {
      console.error(err);
      res.sendStatus(500);
    });
});
```

5°// Conecte-se ao WhatsApp:

-Crie uma nova instância da Client classe do whatsapp-web.js pacote.
-Adicione o seguinte código ao seu server.js arquivo:

## CONEXÃO 
```
const client = new Client();

client.on('qr', qr => {
  // Display the QR code to the user
  console.log('QR Code:', qr);
});

client.on('ready', () => {
  console.log('Client is ready!');
});

client.initialize();
```

6°// Inicie o servidor:

- Adicione o seguinte código ao seu server.js arquivo para iniciar o servidor:

## INIT SERVER
```
const port = 3000; // You can change the port number if needed

app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

7°// Execute o aplicativo:

- Abra seu terminal e navegue até o diretório do projeto.
- Execute o seguinte comando para iniciar o servidor Node.js:

  ## EXECUTAR
```
node server.js
```

Acesse o código QR:

Abra seu navegador da web e visite http://localhost:3000/qr (ou o URL apropriado se você alterou o número da porta).
Você deverá ver o código QR gerado pelo qrcodemódulo.
Conecte sua conta do WhatsApp:

Abra o WhatsApp no seu dispositivo móvel.
Vá para a seção "WhatsApp Web" e escaneie o código QR exibido em seu navegador.
Depois que o código QR for digitalizado e a conexão estabelecida, você pode começar a construir seu bot do WhatsApp ouvindo eventos e respondendo mensagens usando o whatsapp-web.jspacote.

Lembre-se de lidar com erros, implementar lógica de tratamento de mensagens e garantir que o comportamento do bot esteja de acordo com os termos de serviço do WhatsApp.


