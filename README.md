# NEWTRACKS — Landing Pages

Site institucional da **NEWTRACKS**, empresa de rastreamento veicular e monitoramento CFTV sediada em Paranavaí/PR.

## Páginas

| Página | Descrição | Tema |
|--------|-----------|------|
| `/` | Home geral — apresentação da empresa e direcionamento | Cyan + Azul |
| `/rastreamento/` | Rastreamento veicular GPS | Cyan `#2DD4E6` |
| `/monitoramento/` | Monitoramento CFTV | Azul `#3B82F6` |

## Tecnologias

- HTML + CSS + JavaScript puro — zero dependências de build
- [Three.js r128](https://threejs.org/) — globo 3D interativo com drag (rastreamento)
- [GSAP 3.12.5](https://greensock.com/gsap/) + ScrollTrigger — animações de scroll
- Canvas 2D — carro com rota animada, câmeras simuladas, partículas
- [Leaflet.js](https://leafletjs.com/) — mapa interativo na seção de contato

## Estrutura

```
lbnewtracks/
├── index.html              # Home — direciona para as duas páginas
├── rastreamento/
│   └── index.html          # Rastreamento veicular
└── monitoramento/
    └── index.html          # Monitoramento CFTV
```

## Como rodar localmente

Qualquer servidor estático funciona. Com Node.js instalado:

```bash
npx serve . --listen 3000
```

Acesse `http://localhost:3000`

## Deploy

Site 100% estático — compatível com qualquer hospedagem:

- **Vercel** — arrastar a pasta ou conectar o repositório
- **Netlify** — arrastar a pasta ou conectar o repositório  
- **Hostinger / cPanel** — fazer upload via FTP da pasta inteira
- **GitHub Pages** — ativar em Settings → Pages → Branch `main` / `/(root)`

## Contato

**NEWTRACKS**  
Paranavaí · PR  
WhatsApp: [44 9 9174-3336](https://wa.me/5544991743336)
