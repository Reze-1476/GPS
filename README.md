# Dashboard de Sensores em Tempo Real

Página web (HTML + JavaScript puro, sem backend) que exibe os dados brutos de localização e movimento do celular:

- **Geolocation API:** latitude, longitude, altitude, velocidade e **precisão (accuracy)** em metros.
- **DeviceOrientation / DeviceMotion:** bússola digital e acelerômetro.

Funciona em celular e em computador (no computador, bússola e acelerômetro normalmente não existem e o dashboard avisa).

## Arquivos

- `index.html` — dashboard em tempo real.
- `explicacao.html` — página "Como funciona" (trilateração, A-GPS, significado de cada campo).
- `style.css` — estilos compartilhados.

## Testar localmente

A Geolocation API só funciona em HTTPS ou `localhost`:

```powershell
cd "H:\projeto facul"
python -m http.server 8000
```

Abra `http://localhost:8000` no computador. Para testar no celular, publique (abaixo).

## Publicar no GitHub Pages

1. Crie um repositório no GitHub e envie `index.html` e `README.md`.
2. Em **Settings → Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`.
3. O link `https://<usuario>.github.io/<repositorio>/` fica disponível em ~1 minuto (já em HTTPS).

## Roteiro da demonstração (A-GPS)

1. Abrir o link no celular e toca em **Iniciar sensores**, permitindo a localização.
2. Com o **Wi-Fi desligado**, observe o campo **Precisão** (valor alto, ex.: 50–100 m dentro da sala).
3. Peça para **ativar o Wi-Fi**: a precisão deve cair para ~5–20 m, mostrando o A-GPS (satélite + redes terrestres).
4. O histórico no fim da página registra a evolução da precisão.

## Observações

- No iOS, a bússola e o acelerômetro pedem permissão extra (solicitada ao tocar no botão).
- Altitude, velocidade e acelerômetro podem aparecer como `n/d` dependendo do aparelho.
- Na prática, o navegador/SO decide a fonte (GPS, Wi-Fi, torres); o resultado pode variar entre aparelhos.
