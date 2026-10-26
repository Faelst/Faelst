<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=26&pause=1000&color=7C3AED&center=true&vCenter=true&width=600&lines=Ol%C3%A1%2C+eu+sou+o+Rafael+Silverio+%F0%9F%91%8B;Full+Stack+Developer;Node.js+%7C+NestJS+%7C+React+%7C+React+Native;Construindo+o+SafetySwap+%F0%9F%8E%9F%EF%B8%8F" alt="Typing SVG" />

<p>
  <a href="https://github.com/Faelst"><img src="https://img.shields.io/github/followers/Faelst?label=Followers&style=for-the-badge&color=7C3AED&labelColor=1e1e2e" /></a>
  <!-- TODO: troque pelo seu LinkedIn -->
  <a href="https://www.linkedin.com/in/SEU-LINKEDIN"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="mailto:fael_st@hotmail.com"><img src="https://img.shields.io/badge/Email-fael__st@hotmail.com-0078D4?style=for-the-badge&logo=microsoftoutlook&logoColor=white" /></a>
  <a href="https://wa.me/5512981708474"><img src="https://img.shields.io/badge/WhatsApp-+55_12_98170--8474-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" /></a>
  <a href="https://safetyswap.io"><img src="https://img.shields.io/badge/SafetySwap-safetyswap.io-7C3AED?style=for-the-badge&logo=ticket&logoColor=white&labelColor=1e1e2e" /></a>
</p>

</div>

---

### 🧑‍💻 Sobre mim

```ts
const rafael = {
  role: "Full Stack Developer",
  location: "Brasil 🇧🇷",
  stack: {
    backend:  ["Node.js", "NestJS", "Fastify", "Express", "Prisma", "PostgreSQL", "Redis"],
    frontend: ["React", "Next.js", "React Router 7", "TailwindCSS", "React Query", "Zustand"],
    mobile:   ["React Native", "Expo", "expo-router"],
    infra:    ["Docker", "AWS (S3, SNS, SQS)", "RabbitMQ", "Socket.IO"],
  },
  focus: ["Arquitetura limpa", "Sistemas em tempo real", "Pagamentos", "Integrações com WhatsApp"],
  currentlyLearning: "React Router 7 / 8 🚀",
};
```

---

### 🛠️ Tecnologias

<div align="center">

**Linguagens & Back-end**

<img src="https://skillicons.dev/icons?i=ts,js,nodejs,nestjs,express,prisma,postgres,redis&theme=dark" />

**Front-end & Mobile**

<img src="https://skillicons.dev/icons?i=react,nextjs,tailwind,materialui,vite,vitest&theme=dark" />

**Infra & Ferramentas**

<img src="https://skillicons.dev/icons?i=docker,aws,rabbitmq,githubactions,git,linux,postman&theme=dark" />

</div>

---

## 🎟️ Projeto em destaque: SafetySwap

<div align="center">

**Marketplace seguro para revenda de ingressos entre pessoas.**
O comprador paga, o dinheiro fica protegido na plataforma e só é liberado ao vendedor depois que o ingresso é transferido.

<a href="https://safetyswap.io"><img src="https://img.shields.io/badge/Acessar-safetyswap.io-7C3AED?style=for-the-badge" /></a>

</div>

O SafetySwap é um ecossistema completo, com **4 aplicações** que conversam com a mesma API:

| App | Stack | O que faz |
|---|---|---|
| 🧠 **API** | NestJS · Prisma · PostgreSQL · Redis · Socket.IO · Stripe · AWS S3/SNS | Regras de negócio, pagamentos, carteira, disputas e tempo real |
| 🌐 **Web** | Next.js · React Query · Zustand · Tailwind · Zod · Vitest | Plataforma do cliente: comprar, vender e acompanhar pedidos |
| 📱 **Mobile** | React Native · Expo SDK 57 · expo-router · Stripe RN | App iOS/Android com biometria e push notifications |
| 🛡️ **Admin** | Next.js · React Query · Socket.IO | Painel de operação com controle de acesso por papéis e auditoria |

#### ✨ Principais funcionalidades

- 🎫 **Eventos e anúncios**: vitrine de eventos, publicação e gestão de ingressos à venda
- 💬 **Propostas e contrapropostas** entre comprador e vendedor
- 💳 **Checkout com PIX e cartão** (Stripe), com cálculo transparente de taxas para comprador e vendedor
- 🔒 **Pagamento protegido**: pedido com ciclo de vida completo (`PENDING_PAYMENT → PAID → TRANSFERRED → COMPLETED`)
- 👛 **Carteira e saques via PIX**, com chaves PIX cadastradas
- ⚖️ **Central de disputas** com envio de evidências e fila de mediação
- 🪪 **KYC**: verificação de identidade dos usuários
- 🔔 **Notificações em tempo real** (WebSocket + push no mobile)
- 👮 **Painel admin com RBAC** (`OPERATOR`, `ADMIN`, `SUPER_ADMIN`), autorização validada no back-end e trilha de auditoria
- 🤝 **Programa de parceiros**

#### 🏗️ Arquitetura

```text
           ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
           │   Web (Next) │   │ Mobile (Expo)│   │ Admin (Next) │
           └──────┬───────┘   └──────┬───────┘   └──────┬───────┘
                  │     REST + WebSocket (Socket.IO)    │
                  └─────────────────┬───────────────────┘
                           ┌────────▼────────┐
                           │   NestJS API    │  Controller → UseCase → Repository
                           └───┬───┬───┬───┬─┘
               ┌───────────────┘   │   │   └───────────────┐
         ┌─────▼─────┐   ┌─────────▼┐ ┌▼────────┐   ┌──────▼──────┐
         │ PostgreSQL│   │  Redis   │ │ Stripe  │   │ AWS S3 / SNS│
         │ (Prisma)  │   │ (pub/sub)│ │ PIX/card│   │ arquivos/sms│
         └───────────┘   └──────────┘ └─────────┘   └─────────────┘
```

- **Back-end modular** em camadas (Controller → Use Case → Repository), com validação via Zod/class-validator e logs estruturados com Pino
- **Front-end em MVVM** (`View` / `ViewModel` / `services` / `queries` / `mutations`)
- **Tempo real escalável** com Socket.IO + Redis Adapter

---

### 🚀 Outros projetos

| Projeto | Descrição | Stack |
|---|---|---|
| 🐾 [**find-my-pet**](https://github.com/Faelst/find-my-pet) | Plataforma para encontrar e adotar pets | Node.js · React |
| 🏋️ [**api-solid**](https://github.com/Faelst/api-solid) | API seguindo princípios SOLID, com autenticação JWT e testes | Fastify · Prisma · Zod |
| 💬 [**evolution-api**](https://github.com/Faelst/evolution-api) | API REST para integração com WhatsApp | Node.js · Baileys · Prisma · RabbitMQ |
| ⚔️ **match-pvp** | Matchmaking PvP em tempo real | NestJS · Socket.IO · Prisma · JWT |
| ✈️ **FlyZapp** | Plataforma de atendimento multicanal com kanban e filas | Express · Bull · RabbitMQ · React · MUI |

---

### 📊 GitHub Stats

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=Faelst&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Faelst&layout=compact&theme=tokyonight&hide_border=true" />

<img src="https://streak-stats.demolab.com?user=Faelst&theme=tokyonight&hide_border=true" />

</div>

---

### 📫 Contato

<div align="center">

Aberto a oportunidades, freelas e parcerias. Bora conversar! 🤝

| Canal | Contato |
|---|---|
| 📧 **Email** | [fael_st@hotmail.com](mailto:fael_st@hotmail.com) |
| 📱 **WhatsApp** | [+55 (12) 98170-8474](https://wa.me/5512981708474) |
| 💼 **LinkedIn** | [linkedin.com/in/faelst](https://www.linkedin.com/in/faelst/) |
| 🐙 **GitHub** | [github.com/Faelst](https://github.com/Faelst) |

<a href="https://wa.me/5512981708474"><img src="https://img.shields.io/badge/Mande_uma_mensagem-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" /></a>
<a href="mailto:fael_st@hotmail.com"><img src="https://img.shields.io/badge/Envie_um_email-0078D4?style=for-the-badge&logo=microsoftoutlook&logoColor=white" /></a>

</div>

---

<div align="center">

💡 *"Faça funcionar, faça certo, faça rápido."*

<img src="https://komarev.com/ghpvc/?username=Faelst&color=7C3AED&style=flat-square&label=Visitas" />

</div>
