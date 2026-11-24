# Convite de Noivado — clone 1:1

Cópia estática fiel do convite em `https://delma-e-manuel.nosdigital.app/`:
mesmo layout, tipografia, paleta, texturas, fotos, animações e interações.

**Verificação de fidelidade:** capturas full-page normalizadas do original e desta cópia
são **idênticas pixel a pixel** (SHA-256 igual) em 390, 768 e 1440 px de largura.

## Abrir

Duplo clique em `app/index.html` já funciona. Para o comportamento correto de
fontes, áudio e caminhos, serve pela rede local:

```powershell
cd "C:\Users\Admin\Documents\Craft Anything\delma-e-manuel\app"
python -m http.server 8787
```

Depois abre `http://127.0.0.1:8787/`.

## Estrutura

```
app/
  index.html          página completa (HTML + CSS + JS inline, como o original)
  assets/
    padrao.png        estampa africana horizontal (faixas e fundo)
    padrao-v.png      estampa vertical (portas da capa)
    lacre.webp        selo de cera "MH"
    monograma.png     monograma floral M&H
    casal-capa.webp   foto de abertura
    casal-final.webp  foto do encerramento
    foto01–foto11.webp galeria (11 fotos)
    pampas-*.webp     ramos de pampas (creme, terracota, misto)
    bouquet.webp      ramo de flores secas
    musica.mp3        música de fundo (5,8 MB)
    favicon.svg       ícone
    partilha.jpg      imagem de partilha (Open Graph 1200×630)
preview/              capturas do resultado (desktop, tablet, telemóvel, capa)
```

## O que está incluído

- **Capa com portas** que se abrem ao tocar no selo e revelam o convite.
- **Abertura** com parallax na foto, monograma, versículo e ramos animados.
- **Convite** com data (sábado, 26 de dezembro de 2026, 17:30).
- **Contagem decrescente** ao vivo + botão “Guardar na agenda” (Google Calendar).
- **Local** com botão para o Google Maps e “Copiar morada”.
- **Galeria** com 11 fotos: carrinho com snap, setas, pontos, teclado, swipe,
  avanço automático e lightbox em ecrã cheio.
- **Manual do bom convidado** em painel deslizante, com as seis regras e o
  dress code animado.
- **Confirmação de presença (RSVP)** que monta a mensagem e abre o WhatsApp;
  valida o nome, contador de pessoas (1–5), mensagem opcional e memória da
  resposta em `localStorage`.
- **Música** com botão flutuante, pausa automática ao trocar de aba.
- Rodapé, animações de entrada, `prefers-reduced-motion`, foco visível e
  etiquetas ARIA.

## Personalizar

No topo do `<script>` de `app/index.html` existe o bloco `EVENTO`:

```js
const EVENTO = {
  data: '2026-12-26T17:30:00+01:00',
  noivos: 'Miguel & Helma',
  dataTexto: 'Sábado, 26 de Dezembro de 2026, às 17:30',
  whatsapp: '',   // ex.: '244923000000' — sem isto o botão abre o WhatsApp sem destinatário
  maxPessoas: 5
};
```

Para trocar de casal há também texto fixo no HTML que precisa de ser ajustado:
nomes nas várias secções, monograma/selo (imagens), inicial “MH”, data, morada,
link do mapa e link do calendário. O monograma e o selo são imagens — para outro
casal é preciso arte nova.

## Publicar

É um site estático: sobe `app/index.html` e a pasta `app/assets/` para qualquer
alojamento (Netlify, Vercel, GitHub Pages, cPanel, Cloudflare Pages). Não precisa
de build, base de dados nem servidor.

## Notas

- O RSVP não guarda respostas num servidor: abre o WhatsApp com o texto já
  escrito. Para respostas automáticas seria preciso um endpoint/Google Forms.
- As fotos, ilustrações, estampa e música são as do site original. Usa este
  material apenas com autorização de quem detém os direitos.
- O script de analytics da Cloudflare do original foi removido.
- O relógio assume o fuso `+01:00` definido em `EVENTO.data`.
