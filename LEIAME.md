<p align="center">
  <img src="docs/logo.png" alt="TH Guard" width="220">
</p>

<h1 align="center">TH Guard</h1>

<p align="center">
  Verificação de vírus, programas suspeitos e mineradores escondidos para Windows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet" alt=".NET 8">
  <img src="https://img.shields.io/badge/licen%C3%A7a-MIT-green" alt="Licença MIT">
</p>

<p align="center"><a href="README.md">🇺🇸 Read in English</a></p>

---

> O TH Guard **não substitui o antivírus**. Ele usa o **Microsoft Defender** como motor de detecção de vírus e soma verificações próprias para o que antivírus costumam deixar passar: mineradores escondidos, processos disfarçados, persistência na inicialização e configurações de segurança alteradas por malware.

## ✨ Recursos

### 🔍 Verificações
- **Inteligente** (~1 min): processos, mineradores, inicialização, configurações do sistema e extensões do navegador
- **Rápida e completa** do Microsoft Defender, com o andamento ao vivo
- **Pasta ou arquivo**: análise do TH Guard + Microsoft Defender + **VirusTotal** (opcional, com chave gratuita)
- Cada alerta mostra o **nível de risco** (alto, médio, baixo), o motivo, o arquivo e o botão de correção
- "Corrigir todos os altos" com um clique e "Confiar" para esconder alertas que você conhece

### ⛏️ Detecção de mineradores
- Nomes de mineradores conhecidos (XMRig, NiceHash, PhoenixMiner, T-Rex, lolMiner, NBMiner e outros)
- Linhas de comando com pools de mineração, parâmetros de minerador e carteiras de criptomoeda
- Conexões com portas usadas por pools
- **Uso alto de CPU ou placa de vídeo sem janela aberta** por mais de 30 segundos
- Monitor em tempo real que **avisa na hora** quando um possível minerador aparece, mesmo com o app na bandeja
- Mostra há quanto tempo o PC está ocioso (mineradores costumam acelerar nessa hora)

### 🕵️ Processos suspeitos
- Programas com **nome de processo do Windows fora da pasta certa** (ex.: svchost.exe no AppData)
- Nomes **quase iguais** aos do Windows (scvhost, svch0st...)
- **Extensão dupla** (boleto.pdf.exe)
- Assinatura digital ausente ou **adulterada**
- Execução a partir de pastas temporárias, Downloads ou Pública
- Comandos de PowerShell, mshta, rundll32 e certutil usados para baixar ou esconder código

### 🚀 Inicialização (estilo Autoruns)
- Registro (Run/RunOnce), pasta Inicializar, tarefas agendadas (inclusive ocultas), serviços
- **Assinaturas WMI**, sequestro de programas (IFEO), Winlogon alterado e AppInit_DLLs
- Assinatura digital e risco de cada entrada
- **Desativar com backup**, restaurável pela quarentena

### 🛡️ Configurações de segurança
- Antivírus e proteção em tempo real, idade das definições, proteção contra adulteração
- **Exclusões do Defender** (malware adiciona exclusões para se esconder)
- Arquivo **hosts** redirecionando bancos, Windows Update ou antivírus
- **Proxy** desviando a internet, Firewall, UAC, SmartScreen e bloqueio de apps indesejados (PUA)
- Botão de correção em cada item

### 🗃️ Quarentena e histórico
- Arquivos isolados e embaralhados (não executam), com restauração
- Inicializações desativadas também podem ser restauradas
- Histórico de ameaças encontradas pelo Microsoft Defender

### 🎨 Personalização
- Temas escuro, preto e claro, cores de destaque e cor da logo

## 📥 Download

Baixe a versão mais recente em [**Releases**](https://github.com/Thiagosystems/THGuard/releases).

> Não precisa instalar nada: o .exe já inclui o .NET. Funciona no Windows 10/11 64 bits e pede permissão de **administrador**.

## 🛠️ Compilar

Pré-requisito: [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

```bat
git clone https://github.com/Thiagosystems/THGuard.git
cd THGuard
build.bat
```

O executável fica em `publish\THGuard.exe`.

## 📁 Estrutura

| Arquivo | Função |
|---|---|
| `Rules.cs` | Regras: mineradores, pools, processos do Windows, comandos suspeitos |
| `ProcessScanner.cs` | Processos, uso de CPU/GPU e avaliação de risco |
| `StartupScanner.cs` | Tudo que inicia com o Windows |
| `SystemChecks.cs` | Defender, exclusões, hosts, proxy, firewall, UAC, extensões |
| `Defender.cs` | Microsoft Defender, VirusTotal e verificação de pastas |
| `Signatures.cs` | Assinatura digital e hash |
| `Quarantine.cs` | Quarentena e correções |
| `MainWindow.xaml` | Interface |

## ⚠️ Avisos

- Heurísticas podem gerar **falsos positivos**: um alerta é um motivo para olhar com atenção, não uma certeza. Use "Confiar" para programas que você conhece.
- O VirusTotal recebe só o **hash** do arquivo, nunca o arquivo.
- Arquivos da pasta do Windows nunca são colocados em quarentena.

## 📄 Licença

Distribuído sob a licença MIT. Veja [LICENSE](LICENSE).
