---
name: semana
description: Revisão da semana de treino com carga aguda e crônica (ATL, CTL, TSB), treinos feitos e a trava tibial, e sugestão para os próximos dias. Use quando a pessoa pedir um resumo da semana, perguntar como está a carga, se está cansada ou o que fazer amanhã.
argument-hint: "[data de referência AAAA-MM-DD]"
---

# Revisão da semana

1. Chame `get_training_status` do servidor `pulse-kit` com `recent_days: 14` (e a data, se a pessoa deu uma).
2. Se a pessoa prefere outra métrica de carga, repita com `metric: "edwards_trimp"` ou `"polar_cardio_load"` e diga qual está usando.

## O que mostrar

- Uma tabela dos últimos 7 dias: data, treinos (`recentWorkouts`), carga do dia, ATL, CTL e TSB.
- A tendência: CTL subindo, estável ou caindo nas 2 semanas.
- O TSB de hoje e a trava tibial.

## Como ler o TSB

Faixas de uso comum, que são convenção de mercado e não evidência forte:

- acima de +5: descansado, bom para prova ou teste;
- de -10 a +5: manutenção;
- de -10 a -30: bloco de carga produtivo, se o sono e a disposição estão bons;
- abaixo de -30: risco alto de acumular fadiga.

A ATL de 7 dias e a CTL de 42 dias dependem de quanto histórico existe. Com menos de 6 semanas de dados, a CTL está subestimada; diga isso.

## Sugestão para os próximos dias

- Respeite a trava tibial: nada de corrida ou outro impacto antes de `lockedUntilUtc`. Bike, natação e força sem salto podem entrar.
- As ferramentas não veem dor, sono, percepção de esforço nem agenda. Pergunte antes de sugerir carga alta.
- Sugira, não prescreva. Se houver dor que piora de uma semana para outra, recomende avaliação profissional.
