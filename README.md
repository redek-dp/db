### COMO CRIAR APLICATIVO DE CHATBOT USANDO GROK API EM NEXT.JS

Olá, pessoal! Hoje vou te mostrar como criar um aplicativo de chatbot usando a Grok API no Next.js. Vamos lá!
---

Primeiro, crie um novo projeto Next.js. No terminal, execute o comando: `npx create-next-app@latest chatbot-grok`.

Agora, entre na pasta do projeto com `cd chatbot-grok` e inicie o servidor local usando `npm run dev`. Você verá seu app rodando em `http://localhost:3000`.

---
Com o projeto pronto, vamos configurar a Grok API. Acesse o site da Grok, obtenha sua chave de API e salve-a como uma variável de ambiente no arquivo `.env.local`.

```plaintext
NEXT_PUBLIC_GROK_API_KEY=sua_chave_aqui
```

---
Crie uma nova página chamada `chat.js` dentro da pasta `pages`. Aqui, vamos construir a interface do chatbot. Use um formulário simples para capturar mensagens do usuário.

```javascript
import { useState } from 'react';

export default function Chat() {
  const [message, setMessage] = useState('');
  const [response, setResponse] = useState('');

  const sendMessage = async () => {
    const res = await fetch('/api/chat', {
      method: 'POST',
      body: JSON.stringify({ message }),
      headers: { 'Content-Type': 'application/json' },
    });
    const data = await res.json();
    setResponse(data.reply);
  };

  return (
    <div>
      <h1>Chatbot Grok</h1>
      <input
        type="text"
        value={message}
        onChange={(e) => setMessage(e.target.value)}
      />
      <button onClick={sendMessage}>Enviar</button>
      <p>Resposta: {response}</p>
    </div>
  );
}
```

---

Agora, crie um endpoint para integrar a Grok API. Na pasta `pages/api`, adicione um arquivo chamado `chat.js`.
 
```javascript
export default async function handler(req, res) {
  const { message } = req.body;
  const apiKey = process.env.NEXT_PUBLIC_GROK_API_KEY;

  const grokResponse = await fetch('https://api.grok.com/v1/chat', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${apiKey}`,
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({ query: message }),
  });

  const data = await grokResponse.json();
  res.status(200).json({ reply: data.response });
}
```

---
Pronto! Agora você pode testar seu chatbot. Abra o navegador, digite uma mensagem e veja a resposta da Grok API em ação!

---

E é isso! Em poucos passos, você criou um chatbot usando Grok API no Next.js. Personalize conforme necessário e expanda suas ideias.
