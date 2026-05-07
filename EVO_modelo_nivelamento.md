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
- https://pmc.ncbi.nlm.nih.gov/articles/PMC6410796/
- https://link.springer.com/chapter/10.1007/978-3-030-98531-8_3
- https://collej.ai/research
- https://arxiv.org/html/2508.03275v1

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
| completion Rate | >60% dos utilizadores terminam curso |

---

## 🔄 Pseudocódigo do Algoritmo

```
function calcular_nivel(score, nivel_atual, min_score):
    if score >= 85:
        return nivel_atual + 2  # sobe 2 níveis
    elif score >= 70:
        return nivel_atual + 1    # sube 1 nível
    elif score >= 55:
        return nivel_atual        # mantém
    else:
        return nivel_atual - 1    # desce (se > fácil)
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
**Para**: José (colaboração)