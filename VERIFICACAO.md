# Verificação de fidelidade

Objetivo: provar que a cópia é igual ao original, não apenas parecida.

## Método

1. Abrir `https://delma-e-manuel.nosdigital.app/` e a cópia local no mesmo Chrome (157), via CDP.
2. Normalizar os dois lados para o mesmo estado:
   - capa removida e todas as entradas `.rv` / `.escrita` reveladas;
   - animações e transições desligadas;
   - relógio fixo em `07 12 34 45` (o contador ao vivo tornaria a comparação impossível);
   - parallax das fotos removido (`transform: none`);
   - mesma largura de viewport e scrollbar clássica (15 px).
3. Capturar a página inteira com `Page.captureScreenshot` / `captureBeyondViewport`.
4. Comparar os PNGs por SHA-256 e, depois, píxel a píxel.

## Resultado

| Largura | Altura da página | SHA-256 (original = cópia) | Píxeis diferentes |
|--------:|-----------------:|----------------------------|-------------------|
| 1440 px | 6256 px | `31F6BDFC0B19E22BDBC31DF1EAB247426B86496529D645A11A836130D2AF8ECF` | 0 |
| 768 px  | 6256 px | `8833AD5B92FE4E9B356EFA9EFFB565B6025E295E3DC72EB37184A652B0C38467` | 0 |
| 390 px  | 5852 px | `30B7EE10E67248B80E49550F8841AD1FD1AA241C267ECB0599AC271507BD496E` | 0 |

Os seis ficheiros estão em `preview/` (versões da cópia): `desktop-1440.png`,
`tablet-768.png`, `mobile-390.png`.

> As capturas normalizadas têm a capa já aberta e o relógio parado, por isso
> servem para comparar o desenho, não para mostrar a animação.

## Notas

- A base foi o HTML servido pelo site (não o DOM já renderizado), com
  `<!doctype html>` — sem isso o browser entrava em *quirks mode* e a secção da
  contagem ficava 7 px mais baixa.
- Foi removido apenas o script de analytics da Cloudflare.
- O áudio, as fotos e as ilustrações são os ficheiros originais do site.
