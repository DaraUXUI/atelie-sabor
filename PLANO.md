# Plano da landing page — Ateliê do Sabor (v2)

Serve também como contexto para o Claude: cole este arquivo + o Material de apoio no `CLAUDE.md` do projeto.

---

## 1. Contexto de uso (Seção 0)

**Público:** (a) adultos e idosos, e adolescentes a partir de 13 anos, com pouco tempo, que querem sair da rotina, aprender ou investir numa paixão; (b) pais, tios e avós de crianças de 6 a 12 anos, que avaliam a qualidade do curso pelas imagens e pela clareza das informações. Inclui pessoas 50+ e com deficiência visual, auditiva e motora.

**Tarefa principal:** entender qual curso e turma servem e fazer a pré-inscrição.
**Contexto:** principalmente celular, conexão instável, leitura rápida.
**Objetivo:** pré-inscrições (demonstração de interesse, sem reserva de vaga). **CTA primário:** "Fazer pré-inscrição" (por perfil: "Pré-inscrição Essencial" / "Pré-inscrição Kids").

### Requisitos derivados
- Página única, toda em pt-BR, `lang="pt-BR"`.
- Todas as informações do briefing: cursos, módulos, turmas, datas de início, valores, reembolso, certificado, instrutora, contato.
- Formulário com curso e turma, alergias/restrições, dados do participante e do responsável quando necessário.
- Sem back-end: validação, erro e confirmação na própria página; nenhum dado enviado ou armazenado.

### Suposições
- Sem fotos ou vídeos do ateliê: a página usa **6 fotos gratuitas do Unsplash** fornecidas por você (ver seção 4A). Ilustrações em SVG só como apoio (ícones, módulos), se necessário. As fotos podem ser trocadas por fotos reais depois.
- Pré-inscrição = manifestação de interesse; não garante vaga nem cobra nada.

---

## 2. Removido por contrariar o material de apoio
| Item | Motivo |
|---|---|
| Promoção no hero | Sem dado no briefing; preço ou urgência inventados (§10) |
| Depoimentos de responsáveis | Só com dados fornecidos pelo cliente (§10) |
| Vídeo de crianças falando da experiência | Seria prova social inventada; sem material real |
| Vídeo-resumo da edição anterior | Sem material real; exigiria legenda, transcrição e audiodescrição |
| Números de alunos, notas, "turma quase lotada" | Dark patterns / dados não fornecidos |
| Promessa de "vaga garantida" | Não especificado no briefing |

**Como a página inspira sem esses itens:** fotos de cozinha em ação (mãos cortando, panelas, criança e responsável juntos), texto concreto do que se aprende em cada módulo, a instrutora (15 anos de experiência), certificado, reembolso integral e a próxima data de início.

Se o cliente enviar vídeos e depoimentos reais depois, a página já deixa os blocos preparados (comentados no código), mas não ficam visíveis.

---

## 3. Estrutura (Seção 1)

**Header:** skip link → logo (esquerda) → menu: Cursos · Turmas e datas · Instrutora · Dúvidas · Contato · botão "Pré-inscrição".

1. **Hero de entrada:** mosaico de ilustrações mistas (adultos e crianças cozinhando), título, uma frase, e dois botões nativos grandes: **"Para mim (a partir de 13 anos)"** e **"Para uma criança (6 a 12 anos)"**. A escolha só reordena e destaca; sem escolher, a página inteira continua visível.
2. **Estado Adulto/13+:** Culinária Essencial → faixa informativa (próxima turma, dia, preço) com botão → módulos → turmas comparáveis → incluso → instrutora, certificado, reembolso → FAQ → formulário.
3. **Estado Kids:** Culinária Kids (criança + 1 responsável que também cozinha) → ilustrações de aula → módulos → turma → valor por dupla → incluso → instrutora, certificado, reembolso → FAQ → formulário.
4. Em ambos os estados o outro curso aparece como seção secundária.
5. **Rodapé:** endereço, WhatsApp, e-mail, privacidade, nota "dados fictícios".

### Turmas (mesmos atributos, mesma ordem)
| Turma | Dias e horário | Duração | Início | Preço |
|---|---|---|---|---|
| Essencial Manhã | seg e qua, 8h–11h | 4 semanas | 1ª segunda do mês | R$ 480 ou 4x R$ 130 |
| Essencial Noite | ter e qui, 19h–22h | 4 semanas | 1ª terça do mês | R$ 480 ou 4x R$ 130 |
| Essencial Sábado | sáb, 14h–17h | 8 semanas | 1º sábado de fev/abr/jun/ago/out | R$ 480 ou 4x R$ 130 |
| Kids Sábado | sáb, 9h–11h | 8 semanas | 1º sábado de fev/abr/jun/ago/out | R$ 560 por dupla ou 4x R$ 150 |

Próximas datas a partir de 25/10/2026 (conferir): Manhã 02/11/2026 · Noite 03/11/2026 · Sábado e Kids 06/02/2027. Calcular por JS, com texto fixo ("primeira segunda-feira de cada mês") como alternativa. Reembolso integral até 7 dias antes do início.

---

## 4. Direção visual
- Cores quentes (terracota, ocre, verde-oliva, off-white), títulos com serifa, corpo sans ≥ 16 px, line-height 1.5, tokens em CSS.
- Contraste ≥ 4.5:1 (texto) e 3:1 (bordas, foco, ícones).
- Fotos com `alt` descritivo (informativas) ou `alt=""` (decorativas). Sem carrossel, sem autoplay, `prefers-reduced-motion` respeitado.

### 4A. Uso das 6 fotos (originais em `images/1.jpg` a `6.jpg`)
| Foto | Conteúdo | Uso | Alt sugerido |
|---|---|---|---|
| 1 | Criança e mãe cozinhando molho no fogão | **Kids**: hero do estado Kids e mosaico inicial | "Criança despejando molho de tomate numa frigideira, ajudada por uma mulher sorridente" |
| 2 | Casal sorridente cozinhando | **Mosaico inicial** e hero do estado Adulto | "Mulher sorrindo e oferecendo uma colher de pau enquanto um homem corta tomates" |
| 3 | Mãos cortando quiabo, vista de cima | **Módulo "Cortes e técnicas básicas"** (Essencial) | "Mãos cortando quiabo em rodelas sobre uma tábua branca" |
| 4 | Mãos mexendo panela no fogão | **Módulo "Caldos e molhos"** / "Sem experiência? Sem problema" (público 50+) | "Mãos de uma pessoa mais velha mexendo uma panela no fogão" |
| 5 | Cozinha profissional, finalização de pratos | **Instrutora / experiência profissional** (sem afirmar que é a Chef Helena) | "Cozinheiros finalizando pratos sob lâmpadas de cobre numa cozinha profissional" |
| 6 | Mãos cortando tomates-cereja na tábua de bambu | **Seção Essencial** ou bloco "Ingredientes inclusos" | "Mãos cortando tomates-cereja numa tábua de madeira ao lado de legumes" |

**Cuidados:**
- As fotos **não são do ateliê**. Nunca legendar como "nossas aulas" nem "edição anterior"; a página não deve sugerir isso. Colocar crédito "Fotos: Unsplash" no rodapé (não obrigatório, mas honesto) e registrar autores.
- A foto 1 mostra uma criança menor que 6 anos: aceitável como ilustrativa, mas se possível trocar por uma de criança de 6 a 12 anos. Só há **uma** foto de criança, então a seção Kids terá pouca imagem; compensar com texto e ícones.
- Marcas visíveis (Wholesome Meats na 1, Jimmy Dean na 2, Buffalo na 5): recortar ou desfocar para não parecer publicidade ou parceria.
- Otimizar: converter para WebP/AVIF, gerar 2–3 tamanhos, `width/height` e `loading="lazy"` (exceto a do hero), `fetchpriority="high"` no hero.
- Texto sobre foto só com overlay escuro (contraste ≥ 4.5:1).

---

## 5. Formulário (Seção 5), em uma página, agrupado com `fieldset/legend`

1. **Curso e turma** (radio): Essencial Manhã / Noite / Sábado / Kids. Mostra início e valor.
2. **Seus dados** (`autocomplete` name, email, tel): nome, e-mail, WhatsApp (aceita com ou sem máscara).
3. **Participante:**
   - "Sou eu o participante" (reaproveita seus dados, sem pedir de novo) ou dados de outra pessoa (nome, idade; `autocomplete="off"`).
   - **Regra da idade:** o formulário lê a idade informada. Se **menor de 18**, aparece o grupo **Responsável**, com aviso do motivo. No Kids isso vale sempre (idade válida 6–12); no Essencial, idade mínima 13.
4. **Responsável** (só se participante < 18): nome, e-mail, WhatsApp, **grau de parentesco** (select: mãe, pai, avó, avô, tio, tia, outro com campo livre). Opção "Sou o responsável" reaproveita "Seus dados". Não pergunta se vai acompanhar.
5. **Alergias e restrições alimentares** (opcional, "Nenhuma" disponível): explica o uso e pede consentimento específico, separado do aceite geral (LGPD arts. 11 e 14; dados de menores).
6. **Consentimentos** (nunca pré-marcados): privacidade; saúde/criança.
7. **Revisão** com "Editar" por item (curso, turma, início, valor, participante, responsável).
8. **Enviar:** carregamento em até ~400 ms, bloqueia duplo envio.
9. **Confirmação** (`role="status"`): resumo do que foi escolhido + "Recebemos sua pré-inscrição. Você receberá um e-mail para acompanhar a sua inscrição." + explicação de que é manifestação de interesse, sem cobrança nem reserva de vaga + reembolso integral até 7 dias antes + contato (WhatsApp e e-mail).

Erros em três partes (o quê, por quê, como resolver), perto do campo, `aria-invalid` e `aria-describedby`, resumo de erros no topo com links e foco, nunca apagar dados, falha de rede com "Tentar novamente".

> **Atenção:** como a página não tem back-end, nenhum e-mail é de fato enviado. A mensagem de e-mail é o texto previsto para a versão final; no protótipo, mostrar um aviso discreto no formulário e na confirmação ("Protótipo: nenhum dado foi enviado ou armazenado"), para não prometer algo que não acontece.

---

## 6. Sequência de prompts
1. Planejamento: Seção 0 (este documento).
2. Conteúdo: seções 1, 3, 4, 10.
3. Layout e ilustrações: seções 2, 6, 7.
4. Formulário: Seção 5 inteira, com a regra de idade e responsável.
5. Código: seções 8 e 9 + HTML semântico; arquivo único `index.html`.
6. Revisão por outra IA (Seção 11) e Honeycomb (Seção 12).

## 7. Verificação (Seção 11)
Teclado · zoom 200% e 320 px · leitor de tela · Lighthouse/axe/WAVE · contraste · checklist NBR 17225 · revisão cruzada. Registrar o resultado.

## 8. Regras não aplicadas / conflitos
| Regra | Situação | Motivo |
|---|---|---|
| §1 "não forçar escolha" × seletor de perfil | Parcial | Seletor só reordena; nada fica escondido |
| §6 vídeo, legendas, audiodescrição, Libras | Não se aplica | Sem vídeo na página |
| §10 depoimentos | Não aplicado | Sem dados do cliente |
| Mensagem de e-mail × sem back-end | Parcial | Texto previsto, com aviso de protótipo |
