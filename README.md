# URD_APP

**Ground station desktop** da equipe UFABC Rocket Design. Ela reúne num só software tudo o que a equipe usa em campo e no laboratório: **telemetria de voo, testes estáticos de motor, simulação e análise de dados**.

Antes, cada uma dessas tarefas usava um script ou programa diferente. O URD_APP centraliza tudo numa interface gráfica que conversa via serial com os rádios LoRa e com os computadores de bordo ([FlightComputerRTOS](https://github.com/jcardozo08/FlightComputerRTOS)).

## Módulos

| Página | O que faz |
|---|---|
| **GS Flight** | Telemetria de voo em tempo real: gráficos de altitude, posição GPS em mapa online/offline (Leaflet), orientação 3D do foguete e terminal serial. Todos os dados são salvos em log. |
| **GS Flight Rasp** | Variante da ground station com ajustes remotos, como a troca de canal LoRa em voo |
| **GS Static Test** | Ground station para teste estático de motor: empuxo e pressão em tempo real, comando de ignição protegido e teste de comunicação (ping) |
| **Simulator** | Envia ao microcontrolador os dados de um voo real (foguete Arace, IREC 2025), para testar a lógica de voo em solo |
| **Data Analysis** | Carrega logs de voos e de testes estáticos e gera gráficos de desempenho |
| **Map Manager** | Baixa os tiles de mapa da região de lançamento para uso offline em campo |

## Destaques técnicos

- Interface em **PySide6 (Qt 6)**, com gráficos em tempo real usando **pyqtgraph** e visualização 3D com OpenGL
- Comunicação serial (pyserial) em threads separadas, para a interface não travar durante a recepção
- Mapas Leaflet embutidos via Qt WebEngine, com cache offline
- Empacotado como executável Windows com **PyInstaller** (`build.ps1`)

## Como rodar

```bash
pip install -r requirements.txt
python main.py
```

**Stack:** Python · PySide6/Qt · pyqtgraph · NumPy/Pandas/SciPy · pyserial · PyInstaller

> Projeto da equipe **UFABC Rocket Design**, Departamento de Sistemas Embarcados.
