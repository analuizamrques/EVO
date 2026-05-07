**GitHub**: https://github.com/analuizamrques/EVO_lution/blob/main/EVO_modelo_nivelamento.md

# EVO — Sistema de Nivelamento Baseado em Mastery

## 📚 Literatura de Referência

### Princípios Científicos

| Fonte | Conclusão |
|-------|-----------|
| **Spaced Repetition** (PMC, 2019) | Repetições espaçadas melhoram retenção a longo prazo |
| **Adaptive Learning** (Springer, 2022) | Desafia o utilizador no nível certo para permitir crescimento |
| **Mastery-based Progress** (Collej AI, 2024) | +59% performance quando dificuldade progride baseada em domínio |
| **LECTOR** (Arxiv, 2025) | Algoritmo adaptativo para aprendizagem de idiomas |

### Referências
- Spaced Repetition: https://pmc.ncbi.nlm.nih.gov/articles/PMC6410796/
- Adaptive Learning: https://link.springer.com/chapter/10.1007/978-3-030-98531-8_3
- Mastery-based Progress: https://collej.ai/research
- LECTOR: https://arxiv.org/html/2508.03275v1

---

## 🎯 Modelo EVO

### Lógica de Progressão

| Score Obtido | Resultado | Ação |
|------------|---------|------|
| 0-54% | Repete | Mantém + mais prática no mesmo nível |
| 55-69% | Mantém | Permanece no mesmo nível |
| 70-84% | Passa | Avança para próximo nível |
| 85%+ | Sobe 2 | Avança rápido para desafio |

### Min Score por Dificuldade

| Dificuldade | min_score | Sessions |
|-------------|----------|----------|
| Fácil | 55 | 9 |
| Médio | 70 | 20 |
| Desafio | 80 | 10 |

---

## 📊 Performance Tracking

### Colunas em user_progress

| Coluna | Tipo | Descrição |
|--------|------|-----------|
| sequência_acerto | INTEGER | Contagem de acertos consecutivos |
| histórico_níveis | JSONB | Array com níveis anteriores |
| média_score | INTEGER | Média de todos os scores |
| pontuação_total | INTEGER | Score acumulado |
| nível_atual | TEXT | Nível atual (fácil/médio/desafio) |

### Métricas Calculadas

- **Progressão**: Se score ≥ min_score → desbloqueia próxima
- **Regressão**: Se 3+ sessões com <55% → desce nível
- **Motivação**: Se 85%+ em 3 sessões → sobe 2 níveis

---

## 🏆 Resultados Esperados

| Métrica | Meta |
|--------|------|
| Retenção | >70% (vs 30% sem spaced repetition) |
| Engajamento | +36% com adaptive learning |
| Completion Rate | >60% dos utilizadores terminam curso |

---

## 🔄 Pseudocódigo do Algoritmo

```
function calcular_nivel(score, nivel_atual, min_score):
    if score >= 85:
        return nivel_atual + 2  # sobe 2 níveis
    elif score >= 70:
        return nivel_atual + 1    # sobe 1 nível
    elif score >= 55:
        return nivel_atual      # mantém
    else:
        return nivel_atual - 1 # desce (se > fácil)
```

---

## 📝 To-Do para Desenvolvimento

- [ ] Implementar lógica no frontend
- [ ] Testar com usuários reais
- [ ] Ajustar min_score se necessário
- [ ] Adicionar analytics (dashboard)

---

**Última atualização**: 2026-05-07
**Criado por**: Ana & Bea
**Para**: Jose (colaboração)
---

## 🎨 Templates por Dificuldade (Cores EVO)

Cada nível tem uma cor base que identifica visualmente o desafio:

| Template | Cor Base | Hex | Descrição |
|----------|----------|-----|-----------|
| 🌱 Easy | Amarelo | #FFD600 | Calmo, acessível, iniciante |
| 🌿 Medium | Laranja | #FF8C42 | Intermediário, energia |
| 🌟 Challenge | Coral | #FF6B6B | Avançado, desafiante |

### Aplicação nos templates

- **Topbar**: Logo com 3 barras (Amarelo/Laranja/Coral)
- **Step cards**: Background conforme nível
- **Botões play**: Amarelo (#FFD600) com borda preta (#0a0a0a)
- **Progress bar**: Verde (#06D6A0) quando completo

### Padrão Visual

Todos os templates usam:
- Bordas pretas: 2px solid #0a0a0a
- Sombras: 4px 4px 0 #0a0a0a
- Fontes: Space Grotesk (títulos), Inter (corpo)
- Border-radius: 12px-18px

### Estrutura dos Steps (Comum a todos os templates)
1. Contexto (país, missão)
2. Fonética (palavras-chave)
3. Shadowing (repetição em voz)
4. Gramática (regras)
5. Frases (contexto)
6. Desafio (montar frases)
7. Conversação (ChatGPT)
8. Quiz (perguntas)
9. Escrita (produção)
10. Flashcards (revisão)
11. Reveal (vídeo completo)

