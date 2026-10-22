---
name: teste-rampa
description: Conduz e analisa um teste de rampa na bike com o Polar H10 para estimar os limiares ventilatórios (VT1 e VT2) pela DFA alpha-1, sem medidor de potência. Use quando a pessoa quiser descobrir ou revisar zonas e limiares, ou fazer o teste de rampa.
argument-hint: "[caminho da gravação .json ou .fit]"
---

# Teste de rampa por DFA alpha-1

Sem arquivo, explique o protocolo. Com arquivo, analise.

## Protocolo

É preciso uma gravação com todos os intervalos R-R: a exportação de sessão do openPulse (`.json`, protocolo `ramp`) ou um FIT com mensagens HRV. A exportação do Polar Flow não serve, porque descarta o R-R.

1. **Segurança primeiro.** É um teste até perto do máximo. Só faça sem sintomas, sem doença recente e com liberação médica se houver qualquer dúvida. Pare com dor no peito, tontura ou falta de ar desproporcional.
2. Cinta molhada e bem presa. Nada de conversar durante o teste: a fala muda a respiração e o alpha-1.
3. Aquecimento leve de 10 min.
4. Cadência fixa (por exemplo, 90 rpm) e um degrau de resistência a cada 3 min, marcando cada degrau no openPulse. Degraus de 3 min garantem ao menos uma janela limpa de 2 min por nível.
5. Continue até a FC passar com folga do limiar esperado ou a percepção de esforço chegar a 9 de 10.
6. Desaquecimento de 5 min.

## Análise

1. Chame `analyze_recording` com o caminho e `protocol: "ramp"`.
2. Mostre `rampThresholds`: FC no VT1 (alpha-1 0,75) e no VT2 (alpha-1 0,50), o R² e se algum limiar foi extrapolado (fora das FCs atingidas).
3. Mostre `artifactPct` e as janelas de baixa confiança. Com artefatos acima de 3%, o alpha-1 tende a sair enviesado (Rogers et al., 2021).

## Cuidados

- São **estimativas**. Em estudos, a FC no limiar por alpha-1 fica em média perto da medida em laboratório, mas com diferenças individuais de vários bpm.
- Um limiar extrapolado ou um R² baixo (abaixo de 0,7) pede repetir o teste.
- Repita 2 ou 3 vezes em dias parecidos (mesmo horário, descansado) antes de mudar as zonas.
- Sem medidor de potência, o resultado é uma FC de limiar, não uma potência.
