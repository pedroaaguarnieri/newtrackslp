# NEWTRACKS — Dois Sites de Landing Page

## O que é

Dois sites institucionais estáticos para a **NEWTRACKS**, empresa de rastreamento veicular e monitoramento 24h com sede em Paranavaí/PR.

Cada site é **100% auto-contido** — um único `index.html` com CSS e JS inline, sem build, sem bundler. Basta abrir no browser.

---

## Estrutura de arquivos

```
lbnewtracks/
├── rastreamento/
│   └── index.html      # Site 1 — Rastreamento Veicular (cyan)
└── monitoramento/
    └── index.html      # Site 2 — Monitoramento CFTV (electric blue)
```

Cada arquivo é independente. Não há CSS ou JS compartilhado entre eles.

---

## Stack

| Camada | Tecnologia | Versão | Uso |
|--------|-----------|--------|-----|
| Linguagem | HTML + CSS + JS vanilla | — | Tudo inline em cada `index.html` |
| 3D | Three.js | r128 (CDN) | Globo 3D interativo no hero do rastreamento |
| Animações | GSAP + ScrollTrigger | 3.12.5 (CDN) | Reveal on scroll, animações do hero |
| Mapa | Leaflet | 1.9.4 (CDN) | Mapa da seção Contato (ambos os sites) |
| Fontes | Google Fonts | — | Inter, JetBrains Mono, Instrument Serif |

---

## Identidade visual por site

| | Rastreamento | Monitoramento |
|--|--|--|
| **Cor primária** | Cyan `#1FB5C4` / `#2DD4E6` | Electric Blue `#3B82F6` / `#60A5FA` |
| **Glow** | `rgba(45,212,230,0.4)` | `rgba(96,165,250,0.4)` |
| **Fundo** | `#03070D` | `#03070D` |
| **Fontes** | Inter · JetBrains Mono · Instrument Serif | Idem |
| **Visual hero** | Globo 3D Three.js com arcos para 12 cidades BR | Grade 2×2 de câmeras animadas (canvas 2D) |
| **Boot text** | "INICIALIZANDO SISTEMA DE RASTREAMENTO" | "ATIVANDO CENTRAL DE MONITORAMENTO" |
| **Badge hero** | "● RASTREAMENTO ATIVO · 24/7" | "● CENTRAL ATIVA · PROTEÇÃO 24/7" |

---

## Paleta CSS (variáveis em `:root`)

### Rastreamento (cyan)

```css
--accent:        #1FB5C4
--accent-bright: #2DD4E6
--accent-deep:   #0E7A87
--accent-glow:   #5EEEFF
--glow:          rgba(45,212,230,0.4)
--line:          rgba(45,212,230,0.12)
--line-bright:   rgba(45,212,230,0.3)
```

### Monitoramento (electric blue)

```css
--accent:        #3B82F6
--accent-bright: #60A5FA
--accent-deep:   #1D4ED8
--accent-glow:   #93C5FD
--glow:          rgba(96,165,250,0.4)
--line:          rgba(96,165,250,0.12)
--line-bright:   rgba(96,165,250,0.3)
```

### Compartilhado (ambos)

```css
--navy:    #0A1628
--navy-2:  #071120
--navy-deep: #040C18
--ink:     #03070D      /* fundo base */
--cloud:   #E8F0F6      /* texto principal */
--mute:    rgba(232,240,246,0.55)
```

---

## Tipografia

| Fonte | Uso |
|-------|-----|
| **Inter** | Corpo, botões, navegação |
| **JetBrains Mono** | Labels técnicas, badges, índices, footer, HUDs |
| **Instrument Serif italic** | Palavras de destaque nos h1/h2, números de stats |

---

## SITE 1 — Rastreamento (`rastreamento/index.html`)

### Seções em ordem

1. **Boot Loader** — splash com ícone de localização + "INICIALIZANDO SISTEMA DE RASTREAMENTO"
2. **Nav** — logo · switcher de site · links · CTA "Solicitar Proposta"
3. **Hero** — H1 "Cada veículo, cada rota, sob controle." + globo 3D + 3 stats + HUDs
4. **Marquee** — Frotas Corporativas · App iOS e Android · Máquinas Agrícolas · …
5. **Tecnologia** (`#tecnologia`) — bento grid 6 cards: GPS, Chip M2M multioperadora, Bloqueio, Telemetria, Histórico 365d, Cerca Virtual
6. **App Mobile** (`#aplicativo`) — mockup CSS-only do phone com canvas 2D (mapa animado) + 5 features + badges iOS/Android
7. **Serviços** (`#servicos`) — 5 linhas editoriais: Frotas Corporativas, Veículos Particulares, Máquinas Agrícolas, Motos, Cargas & Ativos
8. **Stats Band** — 24/7 · 99.9% · <3s · 365 dias
9. **Processo** (`#processo`) — 4 steps: Contato → Vistoria → Instalação → Ativação no app
10. **CTA** — box com conic-gradient animado + WhatsApp
11. **Contato** (`#contato`) — cards de info + mapa Leaflet
12. **Footer** — 4 colunas + cross-link "Ver também: Monitoramento CFTV →"

### Hero copy
- Badge: `● RASTREAMENTO ATIVO · 24/7`
- H1: "Cada veículo, cada rota, *sob controle.*"
- Stats: 24/7 · 99.9% · <3s

### HUDs do hero
```
LAT  -23.0734    GPS  LOCKED    CHIP  CLARO
LON  -52.4651    SAT  14/16     SINAL  98%
```

### Three.js Globe
- SphereGeometry + wireframe
- 8000 pontos Fibonacci: continentes mais brilhantes sobre América do Sul
- Hub Paranavaí: esfera maior + anel pulsante
- Arcos QuadraticBezierCurve3 para 12 cidades BR com partícula viajando
- Auto-rotação + tilt por mouse (mousemove)

### Chip M2M — bento card
```
CLARO · ATIVO  |  TIM · STANDBY  |  VIVO · STANDBY  |  ALGAR · STANDBY
```
Animação `opPulse` cicla cada badge para estado glow ativo.

### App Mobile — mockup phone
- CSS puro: 280×580px, border-radius:44px, notch, barra de status 9:41, nav 4 abas
- `#phone-canvas`: canvas 2D com grid animado + veículo se movendo
- 5 feature cards com barra de acento à esquerda no hover

---

## SITE 2 — Monitoramento (`monitoramento/index.html`)

### Seções em ordem

1. **Boot Loader** — ícone SVG de câmera + "ATIVANDO CENTRAL DE MONITORAMENTO"
2. **Nav** — logo · switcher de site · links · CTA "Solicitar Orçamento"
3. **Hero** — H1 "Seus olhos, quando você *não está lá.*" + grade 2×2 câmeras canvas + HUDs
4. **Marquee** — CFTV 4K · Alarmes · Portões Elétricos · Câmeras IP · Sensores · Controle de Acesso · Central 24h · Cercas Elétricas
5. **Soluções** (`#solucoes`) — bento grid 6 cards
6. **Para Quem** (`#para-quem`) — 3 colunas: Residencial · Empresarial · Rural/Fazendas
7. **Central 24h** (`#central`) — layout 2 colunas: 4 features + monitor wall visual
8. **Stats Band** — 24/7 · <60s · 4K · 365 dias de gravação
9. **Processo** (`#processo`) — 4 steps: Visita técnica → Projeto → Instalação → Ativação
10. **CTA** — "Segurança que você vê e *sente.*" + WhatsApp
11. **Contato** (`#contato`) — cards de info + mapa Leaflet
12. **Footer** — 4 colunas + cross-link "Ver também: Rastreamento Veicular →"

### Hero copy
- Badge: `● CENTRAL ATIVA · PROTEÇÃO 24/7`
- H1: "Seus olhos, quando você, *não está lá.*"
- Stats: 24/7 · <60s · 4K

### HUDs do hero
```
CAMS  4/4 ONLINE    CENTRAL  PARANAVAÍ
REC   ATIVO         OPR      ONLINE
```

### Câmeras hero (canvas 2D)
- 4 canvas `#cam1` a `#cam4`, cada um com:
  - Fundo escuro `hsl(220,30%,4%)`
  - Grid de linhas finas `rgba(96,165,250,0.04)`
  - Badge "AO VIVO" pulsando em vermelho
  - Timestamp rolando em tempo real (atualizado por `setInterval 1000ms`)
  - Scanline animada descendo
  - CAM-03 tem blob de detecção de movimento + bounding box vermelho

### Bento grid — Soluções
| Card | Span |
|------|------|
| CFTV — Câmeras IP | span-3 tall · SVG cones de cobertura animados |
| Central de Monitoramento | span-3 tall · grid 2×2 de feeds |
| Centrais de Alarme | span-2 |
| Portões Elétricos | span-2 · SVG portão deslizando |
| Sensores | span-2 |
| Controle de Acesso | span-6 |

### Monitor wall — seção Central 24h
- 6 mini-células `#mc1` a `#mc6` com canvas animados
- `mc3` fica em alerta: `border: 1px solid var(--red-live)` piscando
- Barra de alerta: "ALERTA · CAM-03 · MOVIMENTO DETECTADO · OPR: EM ATENDIMENTO"

---

## Navegação entre os dois sites

**Switcher no nav** (pill com estado ativo):
```
[ Rastreamento  |  ◉ Monitoramento ]
```

**Cross-link no footer:**
- Rastreamento → `<a href="../monitoramento/index.html">Ver também: Monitoramento CFTV →</a>`
- Monitoramento → `<a href="../rastreamento/index.html">Ver também: Rastreamento Veicular →</a>`

---

## Animações e JS (padrão em ambos)

### Background
- `#particles-canvas`: canvas 2D com 40 partículas se conectando quando dist < 120px, 60fps

### Scroll (GSAP + ScrollTrigger)
- `.reveal` → `opacity:0; transform:translateY(40px)` por padrão
- GSAP anima para `opacity:1; y:0` + `.in`
- Hero: `delay:1.3` (após boot loader)
- Restante: `scrollTrigger start: 'top 85%'`

### Boot Loader
- `window.addEventListener('load')` → `setTimeout 1200ms` → `#boot.classList.add('done')`
- Transição: `opacity:0; visibility:hidden`

### Mapa (Leaflet)
- Centro: `-23.0734, -52.4651` (Paranavaí), zoom 15
- Tile: OpenStreetMap
- Filtro CSS: `hue-rotate(210deg) invert(.9) saturate(.7)` para tema escuro azul

---

## Dados da empresa

| Campo | Valor |
|-------|-------|
| Nome | NEWTRACKS |
| Endereço | Av. Parigot de Souza, 3660 · Jardim Ibirapuera · Paranavaí/PR |
| Coordenadas | -23.0734, -52.4651 |
| Plus Code | WHG4+6J |
| Telefone / WhatsApp | (44) 99174-3336 |
| Link WhatsApp | `https://wa.me/5544991743336` |
| Horário comercial | Seg–Sex 08:00–18:00 |
| Central monitoramento | 24h |

---

## Convenções do código

- **Tudo em português** — textos, comentários e nomes de seções
- **Sem classes utilitárias** — CSS via seletores semânticos e variáveis
- **CDN apenas** — nenhum npm, nenhum bundler
- **CSS vars para tudo** — nunca cores hardcoded fora do `:root`
- **JS inline no final do `<body>`** — sem módulos ES
- **Responsivo** via `@media (max-width: 1024px)` e `(max-width: 768px)`

---

## Como rodar

Abrir qualquer `index.html` diretamente no browser ou via servidor estático:

```bash
npx serve D:\lbnewtracks --listen 3400
# Rastreamento: http://localhost:3400/rastreamento/
# Monitoramento: http://localhost:3400/monitoramento/
```
