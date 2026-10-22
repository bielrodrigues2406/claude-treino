# claude-treino

Marketplace de plugins do Claude Code para o ecossistema de treino com o Polar H10.

O marketplace se chama `treino-plugins` e o plugin, `treino`. O Claude Code reserva nomes de plugin e de marketplace que começam com `claude-`, por isso eles não repetem o nome do repositório.

## O que o plugin `treino` traz

| Componente | Para quê |
| :--- | :--- |
| Servidor MCP `pulse-kit` | `get_training_status`, `inspect_workout`, `analyze_recording` e `trigger_polar_sync` (código em [pulse-kit](https://github.com/bielrodrigues2406/pulse-kit)) |
| `/treino:analisar-treino [id]` | Análise de um treino da Polar, o último por padrão |
| `/treino:semana [data]` | ATL, CTL e TSB da semana, treinos, trava tibial e sugestão para os próximos dias |
| `/treino:teste-rampa [arquivo]` | Protocolo e análise do teste de rampa por DFA alpha-1 (VT1 e VT2) |
| `/treino:teste-ortostatico [arquivo]` | Protocolo e análise do teste ortostático matinal |
| Agente `fisiologista` | Segunda opinião crítica sobre os números |

## Instalação

1. Compile o servidor:

   ```
   git clone https://github.com/bielrodrigues2406/pulse-kit
   cd pulse-kit
   pnpm install
   pnpm build
   ```

2. Adicione o marketplace e instale o plugin:

   ```
   claude plugin marketplace add bielrodrigues2406/claude-treino
   claude plugin install treino@treino-plugins
   ```

3. No Claude Code, rode `/plugin configure treino@treino-plugins` e preencha:
   - **Pasta do pulse-kit** (obrigatória): o clone do passo 1.
   - **Google** (client id, secret, refresh token e a pasta `Polar_Flow_Sync`): os mesmos do polar-drive-sync. O secret e o token ficam no cofre de credenciais do sistema, não no `settings.json`.
   - **Token do GitHub**: token fine-grained com `Actions: read and write` só no polar-drive-sync, para o `trigger_polar_sync`.
   - **Pasta das gravações do openPulse** e **fuso horário**.

   Os campos opcionais podem ficar vazios; a ferramenta que depender deles avisa o que falta.

4. Confira com `claude mcp list`: deve aparecer `plugin:treino:pulse-kit ... Connected`.

## Validação

```
claude plugin validate ./plugins/treino
claude plugin validate .
```

Os dois passam. A instalação a partir deste diretório também foi testada, e o servidor MCP conecta com a pasta do pulse-kit configurada.
