---
name: teste-ortostatico
description: Teste ortostático matinal com o Polar H10 (deitado e depois em pé) para acompanhar a recuperação pela VFC. Use quando a pessoa quiser saber se está recuperada, fazer o teste da manhã ou ver a tendência de RMSSD.
argument-hint: "[caminho da gravação .json]"
---

# Teste ortostático matinal

## Protocolo

1. Ao acordar, depois de ir ao banheiro, antes do café e do celular.
2. Cinta molhada, deitado de costas, respirando normalmente e sem falar, por 3 min, gravando no openPulse com o protocolo `orthostatic`.
3. Marque `stand` no openPulse e levante. Fique em pé, parado, por 3 min.
4. Faça sempre do mesmo jeito e no mesmo horário: o que vale é a comparação com você mesmo.

## Análise

1. Chame `analyze_recording` com o caminho do arquivo.
2. Mostre `orthostatic`: RMSSD deitado (os 2 min antes de levantar), RMSSD em pé (de 1 a 3 min depois de levantar) e a queda percentual.
3. Mostre `artifactPct`. Acima de 3%, repita o teste outro dia antes de concluir.

## Como interpretar

- Um dia isolado diz pouco: a VFC varia muito de um dia para outro.
- Compare com a média dos últimos 7 dias da própria pessoa. Peça os valores de testes anteriores, se ela tiver.
- RMSSD deitado bem abaixo da média pessoal por vários dias, junto com sono ruim ou cansaço, sugere reduzir a intensidade. Uma queda num dia só, sem outros sinais, não muda o plano.
- Isto não é exame médico e não diagnostica nada.
