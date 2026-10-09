## 1 - Caracterização do protocolo: frequência de trabalho, acesso ao meio (colisão), aplicação/uso
A relação entre PROFINET, PROFIBUS e IO-Link representa a estrutura moderna de pirâmide de automação industrial. Eles não competem entre si; pelo contrário, trabalham juntos para conectar desde a sala de controle até o sensor mais simples na ponta do processo.

1. PROFINET (Nível de Rede Principal / Ethernet): É uma rede baseada em Ethernet Industrial de alta velocidade (≥ 100 Mbit/s). Ela conecta os controladores principais (CLPs) aos módulos de campo, inversores de frequência e Mestres IO-Link.

2. PROFIBUS (Rede de Campo Legada / Serial): É o predecessor do PROFINET, baseado em comunicação serial (RS-485). Embora esteja sendo substituído pelo PROFINET em novas instalações, ainda é amplamente integrado através de proxies ou gateways (como o IE/PB Link) para conversar com redes modernas.

3. IO-Link (Nível de Dispositivo / Ponta): Não é um barramento de rede (fieldbus), mas sim uma conexão ponto a ponto padronizada (IEC 61131-9) de curto alcance (até 20 metros). Ele transforma sensores e atuadores comuns em dispositivos "inteligentes", permitindo enviar múltiplos dados (diagnósticos, temperatura, configuração) através de um cabo comum de 3 fios não blindado


```mermaid
graph TD
    %% Nós Principais
    CLP["💻 CLP / Controlador Central<br>(Siemens, Rockwell, Schneider, etc.)"]
    
    MESTRE["🔌 Mestre IO-Link<br>(Módulo de campo IP67: IFM, Balluff, Siemens)"]
    
    SENSOR["🌡️ Sensor IO-Link<br>(Pressão / Temp / Vazão)"]
    VALVULA["🦾 Válvula IO-Link<br>(Atuador / Bloco de Válvulas)"]
    HUB["🎛️ Hub I/O Digital<br>(Sensores comuns liga/desliga)"]

    %% Conexões com descrições detalhadas
    CLP -- "Cabo PROFINET (Ethernet) ou PROFIBUS" --> MESTRE
    
    MESTRE -- "Cabo Padrão 3 Fios<br>(Até 20 metros / Bidirecional)" --> SENSOR
    MESTRE -- "Cabo Padrão 3 Fios<br>(Até 20 metros / Bidirecional)" --> VALVULA
    MESTRE -- "Cabo Padrão 3 Fios<br>(Conecta sensores binários legados)" --> HUB

    %% Estilização (Classes de Cores)
    classDef nivelControle fill:#1f77b4,stroke:#0f4c75,color:#fff,stroke-width:2px;
    classDef nivelRede fill:#ff7f0e,stroke:#cc5200,color:#fff,stroke-width:2px;
    classDef nivelDispositivo fill:#2ca02c,stroke:#1a661a,color:#fff,stroke-width:2px;

    class CLP nivelControle;
    class MESTRE nivelRede;
    class SENSOR,VALVULA,HUB nivelDispositivo;

```
## 2 - Relação com a pirâmide de automação e indústria 4.0
## 3 - Limites
- Capacidade máxima: números de nós, taxa máxima de transmissão
## 4 - Topologias (Física e lógica)
## 5 - Meios de transmissão: característica física, tipo de cabeamento ou radio/frequência.
## 6 - Compatibilidade - equipamentos, outros protocolos
## 7 - 2 Exemplos (de programação em clp e de uso em supervisórios)