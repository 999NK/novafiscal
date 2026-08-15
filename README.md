<div align="center">
  <img src="imgs/logofull.png" alt="NovaFiscal" width="280" />

  <h1>NovaFiscal</h1>

  <p>
    <strong>Infraestrutura fiscal completa para o Brasil — API-first, multi-tenant e com IA nativa.</strong>
  </p>

  <p>
    Emita, gerencie e automatize documentos fiscais eletrônicos com uma única plataforma.
  </p>

  <p>
    <img src="https://img.shields.io/badge/NestJS-11-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS 11" />
    <img src="https://img.shields.io/badge/Next.js-16-000000?style=for-the-badge&logo=next.js&logoColor=white" alt="Next.js 16" />
    <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
    <img src="https://img.shields.io/badge/Redis-BullMQ-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis" />
    <img src="https://img.shields.io/badge/OpenAI-IA_Fiscal-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI" />
    <img src="https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
  </p>
</div>

---

## 🇧🇷 O que é a NovaFiscal?

A **NovaFiscal** é uma plataforma SaaS de infraestrutura fiscal que resolve a complexidade dos documentos fiscais eletrônicos do Brasil. Com uma API REST completa, IA conversacional integrada e servidor **MCP (Model Context Protocol)** para agentes de IA externos, ela permite que empresas e desenvolvedores emitam documentos fiscais, calculem impostos e automatizem rotinas contábeis — sem se preocupar com webservices SEFAZ, schemas XSD ou assinaturas digitais.

## 📄 Documentos fiscais suportados

| Documento | Descrição |
|-----------|-----------|
| **NF-e** (modelo 55) | Nota Fiscal Eletrônica de mercadorias |
| **NFC-e** (modelo 65) | Nota Fiscal de Consumidor (PDV / varejo), com QR Code |
| **NFS-e** | Nota Fiscal de Serviços (ABRASF + Padrão Nacional) |
| **CT-e** (modelo 57) | Conhecimento de Transporte — 5 modais de frete |           --     { A VALIDAR }
| **MDF-e** (modelo 58) | Manifesto Eletrônico de Documentos Fiscais |              --     { A VALIDAR }
| **DC-e** | Declaração de Conteúdo Eletrônica (remessas) |                         --     { A VALIDAR }
| **SPED** | Escrituração Fiscal Digital (EFD ICMS/IPI e PIS/COFINS) |              --     { A VALIDAR }
| **SINTEGRA** | Operações interestaduais |                                         --     { A VALIDAR }
| **FCI** | Ficha de Conteúdo de Importação |                                       --     { A VALIDAR }

## ✨ O que ela faz

- 🧾 **Emissão completa** — geração de XML, assinatura digital A1, validação XSD e transmissão à SEFAZ
- 🤖 **IA Fiscal conversacional** — emita notas, calcule impostos e consulte CNPJs por linguagem natural (chat web, WhatsApp e Telegram)
- 🛡️ **Simulation-First** — todo documento passa por um gate de simulação que prevê rejeições SEFAZ antes da transmissão, com risk score e sugestões de correção
- 🧮 **Motor tributário híbrido** — impostos legados (ICMS, IPI, PIS, COFINS, ICMS-ST, DIFAL) + Reforma Tributária 2026 (IBS/CBS), detectado automaticamente pela data da operação
- 🔌 **Servidor MCP** — expõe o motor fiscal como ferramentas para Claude, ChatGPT, Cursor, n8n e qualquer agente de IA compatível
- ⚡ **Emissão assíncrona** — resposta imediata à API e processamento em background com filas BullMQ
- 🔄 **Contingência automática** — SVC-AN/SVC-RS ativados quando a SEFAZ-UF fica indisponível, com sincronização ao retorno
- 🏢 **Multi-tenant** — dados, certificados e configurações totalmente isolados por empresa
- 🔔 **Webhooks nativos** — eventos de autorização, rejeição e cancelamento entregues ao seu sistema em tempo real, assinados com HMAC
- 📊 **Dashboard e relatórios** — métricas, faturamento, análise de rejeições, exportação CSV e consolidação mensal
- 🔐 **Segurança de ponta a ponta** — JWT, certificados A1 cifrados com AES-256, rate limiting, idempotência e audit log

## 🛠️ Tecnologias

| Camada | Tecnologia |
|--------|-----------|
| **Backend** | NestJS 11 · TypeScript |
| **Frontend** | Next.js 16 (App Router) · React 19 · Tailwind CSS v4 |
| **Banco de dados** | PostgreSQL (Supabase) · Prisma ORM |
| **Filas assíncronas** | BullMQ · Redis |
| **IA** | OpenAI (function calling com 3 níveis de fallback) |
| **Fiscal** | XML-DSig (RSA-SHA1) · Validação XSD · SOAP/mTLS com SEFAZ |
| **Storage** | Cloudflare R2 / S3 (XMLs e DANFEs) |
| **Documentação** | Swagger / OpenAPI 3.1 em `/docs` |
| **Observabilidade** | OpenTelemetry (Grafana Cloud, Jaeger, Honeycomb) |
| **Infra** | Docker · Docker Compose |

## ⚙️ Como funciona

1. **Cadastre a empresa** — cada tenant tem dados e certificados isolados
2. **Envie o certificado A1** (.pfx) — cifrado com AES-256, usado apenas na hora de assinar
3. **Emita documentos** — via API REST, chat com IA, WhatsApp, Telegram ou agentes MCP
4. **O sistema faz o resto** — calcula impostos, gera e assina o XML, valida, simula o risco de rejeição e transmite à SEFAZ
5. **Acompanhe tudo** — DANFE em PDF, timeline de status, webhooks e relatórios

```
Você → API / IA / WhatsApp → NovaFiscal → SEFAZ
                                  ↓
                    XML + DANFE + Webhooks + SPED
```

> 🧪 **Modo Teste:** emita notas completas sem certificado e sem valor fiscal — ideal para homologação e treinamento.


<div align="center">
  
  <h1>Imagens do sistema</h1>

  <p>
    <a href="https://ibb.co/ffDq17n"><img src="https://i.ibb.co/WZVGx1P/Captura-de-tela-2026-08-15-150511.png" alt="Captura-de-tela-2026-08-15-150511" border="0"></a>
<a href="https://ibb.co/0p9D7RWM"><img src="https://i.ibb.co/8nxKCLR5/Captura-de-tela-2026-08-15-150559.png" alt="Captura-de-tela-2026-08-15-150559" border="0"></a>
<a href="https://ibb.co/tpsWztMD"><img src="https://i.ibb.co/Swn9c8XB/Captura-de-tela-2026-08-15-150622.png" alt="Captura-de-tela-2026-08-15-150622" border="0"></a>
<a href="https://ibb.co/BHzgcxSL"><img src="https://i.ibb.co/My2RZ43n/Captura-de-tela-2026-08-15-150648.png" alt="Captura-de-tela-2026-08-15-150648" border="0"></a>
<a href="https://ibb.co/spsqqpPS"><img src="https://i.ibb.co/GfCRRfJw/Captura-de-tela-2026-08-15-150717.png" alt="Captura-de-tela-2026-08-15-150717" border="0"></a>
<a href="https://ibb.co/tpsWztMD"><img src="https://i.ibb.co/Swn9c8XB/Captura-de-tela-2026-08-15-150622.png" alt="Captura-de-tela-2026-08-15-150622" border="0"></a>
<a href="https://ibb.co/0p9D7RWM"><img src="https://i.ibb.co/8nxKCLR5/Captura-de-tela-2026-08-15-150559.png" alt="Captura-de-tela-2026-08-15-150559" border="0"></a>
<a href="https://ibb.co/BHzgcxSL"><img src="https://i.ibb.co/My2RZ43n/Captura-de-tela-2026-08-15-150648.png" alt="Captura-de-tela-2026-08-15-150648" border="0"></a>
<a href="https://ibb.co/spsqqpPS"><img src="https://i.ibb.co/GfCRRfJw/Captura-de-tela-2026-08-15-150717.png" alt="Captura-de-tela-2026-08-15-150717" border="0"></a>
  </p>
</div>




---

<div align="center">
  <sub>Construído para simplificar a complexidade fiscal do Brasil 🇧🇷</sub>
</div>
