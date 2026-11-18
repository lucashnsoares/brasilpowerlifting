[🇺🇸 English](README.md) | [🇧🇷 Português](README.pt-BR.md)

# Gestão de Torneios Brasil Powerlifting

Sistema 100% offline para gestão de campeonatos de powerlifting e placares em tempo real na rede local (Wi-Fi/LAN), com suporte a **Português (PT-BR)** e **Inglês (EN)**[cite: 3].

> **Prefere o aplicativo pronto para uso sem precisar compilar?**  
> Baixe a versão oficial assinada para Windows na **[Microsoft Store](https://apps.microsoft.com/store/detail/9N79D1086G2W)** para uso não comercial, ou saiba mais em **[brasilpowerlifting.com.br](https://brasilpowerlifting.com.br)**.

---

## Principais Recursos

- **100% Offline:** Funciona localmente com SQLite e backups automáticos — sem depender de internet no dia do campeonato[cite: 3].
- **Dispositivos na Mesma Rede (LAN):** Conecte celulares dos árbitros (`/arbitro`), telão da plateia (`/display`), TV do aquecimento (`/aquecimento`) e pesagem (`/pesagem`) na porta `3000`[cite: 3].
- **Painel Desktop Windows (`PainelPowerlifting.cs`):** Impede a suspensão do Windows, reinicia o servidor automaticamente em caso de falha, detecta o IP da rede Wi-Fi e libera o Firewall com um clique[cite: 3].
- **Nuvem Opcional (Traga sua Própria API):** O código não possui chaves nem URLs privadas embutidas. Clubes sem fins lucrativos podem conectar sua própria API e banco de dados na Central da Nuvem (`/nuvem`)[cite: 3].

---

## Pré-requisitos

- **Node.js (x64, v20 ou superior)** — [Baixar em nodejs.org](https://nodejs.org/)
- **Windows 10/11 (x64)** com .NET Framework 4.x (já incluso no Windows) para compilar o painel desktop[cite: 3, 4]

---

## Como Compilar e Executar a partir do Código-Fonte

### 1. Clonar e Instalar Dependências

```powershell
git clone [https://github.com/lucashnsoares/brasilpowerlifting.git](https://github.com/lucashnsoares/brasilpowerlifting.git)
cd brasilpowerlifting
npm install
```

### 2. Escolher o Modo de Execução

#### Opção A: Execução Rápida via Terminal (Windows, Linux ou macOS)
```bash
node server.js
```
Acesse `http://localhost:3000` no navegador[cite: 3].

#### Opção B: Compilar o Painel Desktop do Windows (`PainelPowerlifting.exe`)

1. **Compile o `PainelPowerlifting.cs` (x64)** usando o compilador nativo do .NET no Windows[cite: 4]:

   ```powershell
   C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe /target:winexe /platform:x64 /optimize+ /out:PainelPowerlifting.exe /win32icon:icone_power.ico PainelPowerlifting.cs
   ```

2. **Copie o `node.exe` para a pasta raiz do projeto:**  
   O `PainelPowerlifting.exe` procura o arquivo `node.exe` na mesma pasta onde está o `server.js`[cite: 3]:

   ```powershell
   Copy-Item (Get-Command node).Source .\node.exe
   ```

3. **Execute o aplicativo:**  
   Abra o `PainelPowerlifting.exe`. O servidor iniciará na porta `3000` e abrirá automaticamente `http://localhost:3000`[cite: 3].

---

## Rede Local (Wi-Fi) e Backups

- Clique em **Liberar Firewall (Wi-Fi)** no painel para liberar a porta TCP `3000` para celulares e Smart TVs na mesma rede[cite: 3].
- O banco de dados e os backups automáticos ficam salvos em `%LOCALAPPDATA%\BrasilPowerlifting`[cite: 2, 3].

---

## Licença (Código Disponível — Uso Não Comercial)

Este projeto é distribuído sob a licença **[PolyForm Noncommercial License 1.0.0](LICENSE.md)**.

- **Uso gratuito permitido:** Uso pessoal, campeonatos amadores, eventos beneficentes e clubes universitários ou sem fins lucrativos (incluindo cobrança de taxa de inscrição exclusivamente para custear a estrutura do evento).
- **Uso comercial:** Federações e eventos com fins lucrativos devem adquirir uma licença entrando em contato pelo [brasilpowerlifting.com.br](https://brasilpowerlifting.com.br).