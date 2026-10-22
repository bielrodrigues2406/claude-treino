---
name: analisar-treino
description: Analisa um treino da Polar sincronizado no Drive (o último, ou um id dado) com o servidor MCP pulse-kit. Use quando a pessoa pedir para ver, analisar ou comentar um treino, uma corrida, um pedal ou a FC de uma sessão.
argument-hint: "[id do treino da Polar]"
---

# Analisar um treino

Use as ferramentas do servidor MCP `pulse-kit` deste plugin.

1. Se a pessoa acabou de treinar, ou o treino pedido não aparece, chame `trigger_polar_sync` e espere terminar. O sync roda sozinho duas vezes por dia, então um treino de agora pode ainda não estar no Drive.
2. Chame `get_training_status` com `recent_days: 7`. Se nenhum id foi dado, use o primeiro de `recentWorkouts`, que é o mais recente.
3. Chame `inspect_workout` com o id.

## Como apresentar

Escreva em português, curto, com os números que importam:

- duração, FC média e máxima, FC por quarto do tempo;
- tempo em cada zona da Polar;
- deriva de FC (`driftPct`) e o que ela significa neste treino;
- carga: Edwards (`edwardsTrimp`) e o cardio load da Polar;
- pausas ou perdas de sinal (`gaps`) acima de 30 s;
- o estado para o dia seguinte: TSB e a trava tibial (`impact`).

## Cuidados de interpretação

- **A deriva é só de FC.** Ela compara a segunda metade com a primeira, depois de 10 min de aquecimento. Só indica desacoplamento em esforço constante (esteira em ritmo fixo, rolo em carga fixa). Em treino intervalado ou progressivo, diga que a deriva não se aplica. Pergunte o ritmo ou a potência quando fizer diferença.
- **Faixas de referência são heurísticas.** Abaixo de 5% em esforço constante costuma indicar boa base aeróbia; acima disso, calor, hidratação, sono e fadiga explicam mais do que o condicionamento. Não trate como diagnóstico.
- **A trava tibial de 48 h é uma regra pessoal**, não critério clínico. Informe o horário de liberação (`lockedUntilUtc`) no fuso local.
- Se `hr_valid_ratio` for baixo ou houver muitas pausas, avise que a cinta pode ter perdido contato e que os números ficam menos confiáveis.
- Não invente o que a ferramenta não devolveu (ritmo, potência, percepção de esforço). Pergunte.
