# 🥊 AdTube vs. ZenStream: A Batalha do Layout Shift (CLS)

> Um estudo prático (e satírico) sobre Core Web Vitals, UX e por que botões que fogem do mouse são a ruína da internet.

🔗 **[Acesse a Demonstração Online](https://eliasolie.github.io/cls/)** *(Substitua pelo seu link do Pages)*

---

## 📖 Sobre o Projeto

Este projeto foi desenvolvido para ilustrar visualmente um dos problemas mais frustrantes da web moderna: o **Cumulative Layout Shift (CLS)**. 

Através de duas versões da mesma interface, demonstramos como a falta de planejamento no carregamento de ativos (especialmente anúncios) impacta a usabilidade e a conversão.

O projeto é dividido em dois cenários:
1.  **AdTube (O Problema):** Uma plataforma caótica onde elementos saltam na tela.
2.  **ZenStream (A Solução):** Uma implementação estável usando boas práticas de front-end.

---

## 🛑 Cenário 1: AdTube (Bad UX)

O AdTube simula um site que prioriza a injeção de anúncios sem reservar espaço no DOM.

### O que acontece aqui?
* **Comportamento:** Ao passar o mouse sobre um vídeo (intenção de clique), um script simula o carregamento tardio de um banner.
* **O Resultado:** O banner empurra o conteúdo para baixo ou para o lado instantaneamente.
* **A Consequência:** O usuário sofre um *Miss-click* (clique errado), clicando no anúncio contra sua vontade.

### 🧠 Conceito Técnico: CLS (Cumulative Layout Shift)
O CLS é uma métrica do **Google Core Web Vitals** que mede a estabilidade visual. 
* No AdTube, o CLS é **alto** (ruim). 
* O navegador não sabe o tamanho do elemento que vai entrar, então ele "reflow" (recalcula) todo o layout quando o elemento aparece, deslocando o conteúdo visível.

---

## ✅ Cenário 2: ZenStream (Good UX)

O ZenStream apresenta a correção técnica para o problema, mantendo a receita de anúncios sem sacrificar o usuário.

### As Soluções Implementadas

#### 1. Reserva de Espaço (Aspect Ratio & Fixed Dimensions)
No CSS, definimos explicitamente o espaço que o anúncio ocupará **antes** dele carregar.
```css
.ad-slot {
    min-height: 100px; /* O espaço está reservado */
    width: 100%;
}
```
Isso garante que, mesmo que o anúncio demore 5 segundos para aparecer, o conteúdo ao redor permanece imóvel. CLS = 0.

#### 2. Skeleton Screens (UI de Carregamento)
Em vez de um espaço em branco ou um "pulo" repentino, usamos um Skeleton (esqueleto) animado.

Função: Reduz a ansiedade do usuário e indica que algo será carregado ali.

UX: Melhora a percepção de performance (Perceived Performance).

## 🛠️ Tecnologias Utilizadas
HTML5 Semântico

CSS3: Grid Layout, Flexbox, Animations (para o Skeleton) e Variáveis (CSS Custom Properties).

JavaScript (Vanilla): Utilizado apenas para simular a latência de rede (setTimeout) e demonstrar o comportamento assíncrono de anúncios reais.

## 🚀 Como Rodar Localmente
Clone este repositório:

```Bash
git clone [https://github.com/EliasOlie/cls.git]([https://github.com/SEU-USUARIO/NOME-DO-REPO.git](https://github.com/EliasOlie/cls.git))
```
Abra o arquivo index.html em qualquer navegador.

Escolha entre sentir raiva (AdTube) ou sentir paz (ZenStream).

## 👨‍💻 Autor
Desenvolvido para conscientizar desenvolvedores e empresários de que Performance é UX.
Este projeto é uma sátira educativa. Nenhum usuário real foi forçado a clicar em anúncios de remédio para calvície durante o desenvolvimento.
