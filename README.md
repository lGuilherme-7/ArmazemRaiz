# 🏗️ Armazém Raiz — Catálogo Digital para Materiais de Construção

> Site institucional moderno, responsivo e funcional — desenvolvido com HTML, CSS e JavaScript puro, sem dependências externas.

---

## 📋 Sobre o Projeto

O **Armazém Raiz** é um sistema de catálogo digital para depósito de materiais de construção com carrinho de orçamentos integrado e finalização via WhatsApp. Desenvolvido como um único arquivo `index.html`, não requer servidor, framework ou instalação.

---

## 🌐 Link para acessar

https://lguilherme-7.github.io/armazemRaiz/

---

## ✨ Funcionalidades

- **Catálogo de produtos** com nome, descrição, preço, unidade e imagem
- **Categorias** separadas: Cimento e Argamassa, Tijolos e Blocos, Ferramentas, Elétrica, Hidráulica, Acabamento e EPI/Segurança
- **Filtro por categoria** com botões dinâmicos gerados a partir dos dados
- **Busca em tempo real** por nome e categoria do produto
- **Carrinho de orçamentos** com:
  - Adição e remoção de itens
  - Controle de quantidade por produto
  - Cálculo automático de total estimado
  - Persistência via LocalStorage (orçamento salvo ao fechar o navegador)
- **Finalizar orçamento pelo WhatsApp** com mensagem formatada automaticamente
- **Geolocalização** — calcula distância até o depósito e gera rota no Google Maps
- **Seção de depoimentos** de clientes reais
- **Seção de vantagens** com diferenciais do negócio
- **Barra de promoções** fixa com informações de entrega e pagamento
- **Toasts de feedback** para ações do usuário
- **Design responsivo** (mobile first) com menu hambúrguer para mobile

---

## 🗂️ Estrutura do Projeto

```
armazem-raiz/
└── index.html        # Aplicação completa (HTML + CSS + JS em um único arquivo)
```

O projeto é intencionalmente um arquivo único para facilitar deploy e distribuição. O código interno está organizado em três blocos bem delimitados por comentários:

| Bloco | Localização | Conteúdo |
|---|---|---|
| HTML | `<body>` | Estrutura e marcação semântica |
| CSS | `<style>` | Estilos, variáveis e responsividade |
| JS | `<script>` | Dados, lógica e interatividade |

---

## 🚀 Como Usar

**1. Clone ou baixe o projeto:**
```bash
git clone https://github.com/seu-usuario/armazem-raiz.git
```

**2. Abra o arquivo no navegador:**
```bash
# Simplesmente abra o arquivo:
open index.html

# Ou com um servidor local (opcional):
npx serve .
```

Não é necessário instalar nada. Funciona offline diretamente no navegador.

---

## ⚙️ Configuração

### Número do WhatsApp

No arquivo `index.html`, localize os links com `api.whatsapp.com` e altere o número de telefone (com DDI + DDD, sem espaços ou caracteres especiais):

```html
<a href="https://api.whatsapp.com/send?phone=5535991234567">...</a>
```

A função `finalizarPedido()` no bloco `<script>` também possui o número configurável:

```javascript
const WHATSAPP = '5535991234567'; // ← Altere aqui
//               55 = Brasil | 35 = DDD | número
```

### Produtos e Catálogo

Os produtos estão definidos no array `PRODUCTS` no bloco `<script>`. Cada item segue esta estrutura:

```javascript
{
  id: 1,                          // ID único (número)
  name: 'Cimento CP-II 50kg',     // Nome do produto
  category: 'cimento',            // Categoria (chave do CAT_LABELS)
  price: 38.90,                   // Preço (número)
  unit: 'saco 50kg',              // Unidade de medida
  img: 'https://...'              // URL da imagem
}
```

### Categorias

As categorias são configuradas no objeto `CAT_LABELS`. Os botões de filtro são gerados automaticamente a partir dos dados:

```javascript
const CAT_LABELS = {
  cimento:     '🏗️ Cimento e Argamassa',
  alvenaria:   '🧱 Tijolos e Blocos',
  ferramentas: '🔧 Ferramentas',
  eletrica:    '⚡ Elétrica',
  hidraulica:  '🚿 Hidráulica',
  acabamento:  '🪟 Acabamento',
  seguranca:   '🦺 EPI e Segurança',
};
```

Para adicionar uma nova categoria, basta incluir a entrada aqui e adicionar produtos com a nova chave.

### Localização do Depósito

A geolocalização calcula a distância até as coordenadas do depósito. Altere no script:

```javascript
// Coordenadas do depósito (lat, lon)
const dist = calcDist(latitude, longitude, -22.6578, -45.8603);
//                                          ↑ latitude  ↑ longitude
```

---

## 🎨 Tecnologias

| Tecnologia | Uso |
|---|---|
| HTML5 semântico | Estrutura e acessibilidade |
| CSS3 (variáveis, grid, flexbox) | Layout e design responsivo |
| JavaScript ES6+ | Lógica, DOM e LocalStorage |
| Google Fonts (Inter + Barlow) | Tipografia |
| Unsplash | Imagens dos produtos |
| Nominatim (OpenStreetMap) | Geocodificação reversa |

Sem frameworks, sem bundlers, sem dependências de terceiros.

---

## 📱 Responsividade

| Breakpoint | Layout |
|---|---|
| `> 1024px` | Grid 5+ colunas, sidebar nav visível, layout full |
| `768px – 1024px` | Grid 3–4 colunas, nav visível |
| `560px – 768px` | Grid 2–3 colunas, menu hamburger |
| `< 560px` | Grid 2 colunas, layout mobile compacto |

---

## 🔧 Personalização Rápida

**Alterar as cores principais** — edite as variáveis CSS no topo do `<style>`:

```css
:root {
  --orange-600: #d95f02;  /* Cor primária / CTAs */
  --orange-500: #f07030;  /* Hover / estados ativos */
  --navy-900:   #131a24;  /* Header do carrinho, sidebar footer */
  --navy-800:   #1a2535;  /* Fundo de cards escuros */
  --gray-50:    #f8f9fb;  /* Fundo da página */
}
```

**Alterar informações de contato** — pesquise e substitua no arquivo:

```
(35) 99123-4567               → seu telefone
vendas@depositoalicerce.com.br → seu e-mail
Av. Industrial, 1.250          → seu endereço
Gonçalves, MG                  → sua cidade
```

---

## 📦 Deploy

Por ser um único arquivo estático, o Armazém Raiz pode ser hospedado em qualquer serviço:

- **GitHub Pages** — suba o repositório e ative Pages na branch `main`
- **Netlify / Vercel** — arraste a pasta para o dashboard
- **Qualquer hospedagem compartilhada** — upload via FTP

---

## 📄 Licença

Este projeto está sob a licença MIT. Sinta-se livre para usar, modificar e distribuir.

---

Feito com 🧱 e muito concreto.
