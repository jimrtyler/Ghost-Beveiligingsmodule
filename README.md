# 👻 Ghost Security Module
**PowerShell-Gebaseerde Windows & Azure Beveiligingsharding**

> **Proactieve beveiligingsharding voor Windows-eindpunten en Azure-omgevingen.** Ghost biedt PowerShell-gebaseerde hardingfuncties die kunnen helpen bij het verminderen van veelvoorkomende aanvalsvectoren door onnodige services en protocollen uit te schakelen.

## ⚠️ Belangrijke Disclaimers

**TESTEN VEREIST**: Test Ghost altijd eerst in niet-productieomgevingen. Het uitschakelen van services kan legitieme bedrijfsfuncties beïnvloeden.

**GEEN GARANTIES**: Hoewel Ghost zich richt op veelvoorkomende aanvalsvectoren, kan geen beveiligingstool alle aanvallen voorkomen. Dit is één onderdeel van een uitgebreide beveiligingsstrategie.

**OPERATIONELE IMPACT**: Sommige functies kunnen de systeemfunctionaliteit beïnvloeden. Beoordeel elke instelling zorgvuldig voor implementatie.

**PROFESSIONELE BEOORDELING**: Voor productieomgevingen, raadpleeg beveiligingsprofessionals om ervoor te zorgen dat instellingen aansluiten bij de behoeften van uw organisatie.

## 📊 Het Beveiligingslandschap

Ransomware-schade bereikte **$57 miljard in 2025**, waarbij onderzoek aantoont dat veel succesvolle aanvallen gebruik maken van basis Windows-services en verkeerde configuraties. Veelvoorkomende aanvalsvectoren omvatten:

- **90% van ransomware-incidenten** betreft RDP-exploitatie
- **SMBv1-kwetsbaarheden** maakten aanvallen zoals WannaCry en NotPetya mogelijk
- **Documentmacro's** blijven een primaire malware-leveringsmethode
- **USB-gebaseerde aanvallen** blijven zich richten op air-gapped netwerken
- **PowerShell-misbruik** is de afgelopen jaren aanzienlijk toegenomen

## 🛡️ Ghost Beveiligingsfuncties

Ghost biedt **16 Windows-hardingfuncties** plus **Azure-beveiligingsintegratie**:

### Windows Eindpunt-harding

| Functie | Doel | Overwegingen |
|---------|------|-------------|
| `Set-RDP` | Beheert Remote Desktop-toegang | Kan externe administratie beïnvloeden |
| `Set-SMBv1` | Controleert legacy SMB-protocol | Vereist voor zeer oude systemen |
| `Set-AutoRun` | Controleert AutoPlay/AutoRun | Kan gebruikersgemak beïnvloeden |
| `Set-USBStorage` | Beperkt USB-opslagapparaten | Kan legitiem USB-gebruik beïnvloeden |
| `Set-Macros` | Controleert Office-macro-uitvoering | Kan macro-ingeschakelde documenten beïnvloeden |
| `Set-PSRemoting` | Beheert PowerShell-remoting | Kan extern beheer beïnvloeden |
| `Set-WinRM` | Controleert Windows Remote Management | Kan externe administratie beïnvloeden |
| `Set-LLMNR` | Beheert naamresolutieprotocol | Meestal veilig om uit te schakelen |
| `Set-NetBIOS` | Controleert NetBIOS over TCP/IP | Kan legacy-applicaties beïnvloeden |
| `Set-AdminShares` | Beheert administratieve shares | Kan externe bestandstoegang beïnvloeden |
| `Set-Telemetry` | Controleert gegevensverzameling | Kan diagnostische mogelijkheden beïnvloeden |
| `Set-GuestAccount` | Beheert gastaccount | Meestal veilig om uit te schakelen |
| `Set-ICMP` | Controleert ping-reacties | Kan netwerkdiagnostiek beïnvloeden |
| `Set-RemoteAssistance` | Beheert externe hulp | Kan helpdesk-operaties beïnvloeden |
| `Set-NetworkDiscovery` | Controleert netwerkdetectie | Kan netwerkbrowsing beïnvloeden |
| `Set-Firewall` | Beheert Windows Firewall | Kritiek voor netwerkbeveiliging |

### Azure Cloud Beveiliging

| Functie | Doel | Vereisten |
|---------|------|-----------|
| `Set-AzureSecurityDefaults` | Schakelt basis Azure AD-beveiliging in | Microsoft Graph-machtigingen |
| `Set-AzureConditionalAccess` | Configureert toegangsbeleid | Azure AD P1/P2-licenties |
| `Set-AzurePrivilegedUsers` | Controleert bevoorrechte accounts | Globale beheerdersmachtigingen |

### Enterprise Implementatieopties

| Methode | Gebruiksgeval | Vereisten |
|---------|---------------|-----------|
| **Directe Uitvoering** | Testen, kleine omgevingen | Lokale beheerdersrechten |
| **Group Policy** | Domeinomgevingen | Domeinbeheerder, GP-beheer |
| **Microsoft Intune** | Cloud-beheerde apparaten | Intune-licenties, Graph API |

## 🚀 Snel Starten

### Beveiligingsbeoordeling
```powershell
# Laad Ghost-module
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Controleer huidige beveiligingspositie
Get-Ghost
```

### Basis Harding (Test Eerst)
```powershell
# Essentiële harding - test eerst in lab-omgeving
Set-Ghost -SMBv1 -AutoRun -Macros

# Bekijk wijzigingen
Get-Ghost
```

### Enterprise Implementatie
```powershell
# Group Policy-implementatie (domeinomgevingen)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune-implementatie (cloud-beheerde apparaten)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Installatiemethoden

### Optie 1: Directe Download (Testen)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Optie 2: Module-installatie
```powershell
# Installeer vanuit PowerShell Gallery (wanneer beschikbaar)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Optie 3: Enterprise Implementatie
```powershell
# Kopieer naar netwerklocatie voor Group Policy-implementatie
# Configureer Intune PowerShell-scripts voor cloud-implementatie
```

## 💼 Gebruikscasevoorbeelden

### Klein Bedrijf
```powershell
# Basisbescherming met minimale impact
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Zorgomgeving
```powershell
# HIPAA-gerichte harding
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Financiële Diensten
```powershell
# Hoge beveiligingsconfiguratie
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-First Organisatie
```powershell
# Intune-beheerde implementatie
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 📝 Functiedetails

### Kern Hardingfuncties

#### Netwerkservices
- **RDP**: Blokkeert remote desktop-toegang of randomiseert poort
- **SMBv1**: Schakelt legacy bestandsdelingsprotocol uit
- **ICMP**: Voorkomt ping-reacties voor verkenning
- **LLMNR/NetBIOS**: Blokkeert legacy naamresolutieprotocollen

#### Applicatiebeveiliging
- **Macro's**: Schakelt macro-uitvoering uit in Office-applicaties
- **AutoRun**: Voorkomt automatische uitvoering van verwisselbare media

### Extern Beheer
- **PSRemoting**: Schakelt PowerShell-externe sessies uit
- **WinRM**: Stopt Windows Remote Management
- **Externe Hulp**: Blokkeert externe hulpverbindingen

#### Toegangscontrole
- **Admin Shares**: Schakelt C$, ADMIN$ shares uit
- **Gastaccount**: Schakelt gasttoegang uit
- **USB-opslag**: Beperkt USB-apparaatgebruik

### Azure Integratie
```powershell
# Verbind met Azure-tenant
Connect-AzureGhost -Interactive

# Schakel beveiligingsstandaarden in
Set-AzureSecurityDefaults -Enable

# Configureer voorwaardelijke toegang
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Controleer bevoorrechte gebruikers
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integratie (Nieuw in v2)
```powershell
# Verbind met Intune
Connect-IntuneGhost -Interactive

# Implementeer via Intune-beleid
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Belangrijke Overwegingen

### Testvereisten
- **Lab-omgeving**: Test alle instellingen eerst in geïsoleerde omgeving
- **Gefaseerde Implementatie**: Rol geleidelijk uit om problemen te identificeren
- **Rollback-plan**: Zorg ervoor dat u wijzigingen kunt terugdraaien indien nodig
- **Documentatie**: Registreer welke instellingen werken voor uw omgeving

### Potentiële Impact
- **Gebruikersproductiviteit**: Sommige instellingen kunnen dagelijkse workflows beïnvloeden
- **Legacy-applicaties**: Oudere systemen kunnen bepaalde protocollen vereisen
- **Externe toegang**: Overweeg impact op legitieme externe administratie
- **Bedrijfsprocessen**: Controleer of instellingen kritieke functies niet verstoren

### Beveiligingsbeperkingen
- **Defense in Depth**: Ghost is één beveiligingslaag, geen complete oplossing
- **Doorlopend Beheer**: Beveiliging vereist continue monitoring en updates
- **Gebruikerstraining**: Technische controles moeten gepaard gaan met beveiligingsbewustzijn
- **Dreigingevolutie**: Nieuwe aanvalsmethoden kunnen huidige bescherming omzeilen

## 🎯 Voorbeeld Aanvalsscenario's

Hoewel Ghost zich richt op veelvoorkomende aanvalsvectoren, hangt specifieke preventie af van juiste implementatie en testing:

### WannaCry-achtige Aanvallen
- **Mitigatie**: `Set-Ghost -SMBv1` schakelt het kwetsbare protocol uit
- **Overweging**: Zorg ervoor dat geen legacy-systemen SMBv1 vereisen

### RDP-gebaseerde Ransomware
- **Mitigatie**: `Set-Ghost -RDP` blokkeert remote desktop-toegang
- **Overweging**: Kan alternatieve externe toegangsmethoden vereisen

### Document-gebaseerde Malware
- **Mitigatie**: `Set-Ghost -Macros` schakelt macro-uitvoering uit
- **Overweging**: Kan legitieme macro-ingeschakelde documenten beïnvloeden

### USB-geleverde Bedreigingen
- **Mitigatie**: `Set-Ghost -USBStorage -AutoRun` beperkt USB-functionaliteit
- **Overweging**: Kan legitiem USB-apparaatgebruik beïnvloeden

## 🏢 Enterprise Functies

### Group Policy Ondersteuning
```powershell
# Pas instellingen toe via Group Policy-register
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Instellingen worden domeinbreed toegepast na GP-vernieuwing
gpupdate /force
```

### Microsoft Intune Integratie
```powershell
# Maak Intune-beleid voor Ghost-instellingen
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Beleid wordt automatisch geïmplementeerd op beheerde apparaten
```

### Compliance Rapportage
```powershell
# Genereer beveiligingsbeoordelingsrapport
Get-Ghost | Export-Csv -Path "BeveiligingsAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure beveiligingspostuurrrapport
Get-AzureGhost | Out-File "AzureBeveiligingsRapport.txt"
```

## 📚 Beste Praktijken

### Pre-implementatie
1. **Documenteer Huidige Staat**: Voer `Get-Ghost` uit voor wijzigingen
2. **Test Grondig**: Valideer in niet-productieomgeving
3. **Plan Rollback**: Weet hoe elke instelling terug te draaien
4. **Stakeholder Review**: Zorg ervoor dat bedrijfseenheden wijzigingen goedkeuren

### Tijdens Implementatie
1. **Gefaseerde Aanpak**: Implementeer eerst naar pilotgroepen
2. **Monitor Impact**: Let op gebruikersklachten of systeemproblemen
3. **Documenteer Problemen**: Registreer eventuele problemen voor toekomstige referentie
4. **Communiceer Wijzigingen**: Informeer gebruikers over beveiligingsverbeteringen

### Na Implementatie
1. **Regelmatige Beoordeling**: Voer periodiek `Get-Ghost` uit om instellingen te verifiëren
2. **Update Documentatie**: Houd beveiligingsconfiguraties actueel
3. **Beoordeel Effectiviteit**: Monitor voor beveiligingsincidenten
4. **Continue Verbetering**: Pas instellingen aan op basis van dreigingslandschap

## 🔧 Probleemoplossing

### Veelvoorkomende Problemen
- **Machtigingsfouten**: Zorg voor verhoogde PowerShell-sessie
- **Service-afhankelijkheden**: Sommige services kunnen afhankelijkheden hebben
- **Applicatiecompatibiliteit**: Test met bedrijfsapplicaties
- **Netwerkconnectiviteit**: Controleer of externe toegang nog steeds werkt

### Hersteloptiers
```powershell
# Heractiveer specifieke services indien nodig
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Over de Auteur

**Jim Tyler** - Microsoft MVP voor PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ abonnees)
- **Nieuwsbrief**: [PowerShell.News](https://powershell.news) - Wekelijkse beveiligingsintelligentie
- **Auteur**: "PowerShell for Systems Engineers"
- **Ervaring**: Decennia van PowerShell-automatisering en Windows-beveiliging

## 📄 Licentie & Disclaimer

### MIT Licentie
Ghost wordt geleverd onder de MIT-licentie voor vrij gebruik, wijziging en distributie.

### Beveiligingsdisclaimer
- **Geen Garantie**: Ghost wordt "as-is" geleverd zonder garantie van welke aard dan ook
- **Testen Vereist**: Test altijd eerst in niet-productieomgevingen
- **Professionele Begeleiding**: Raadpleeg beveiligingsprofessionals voor productie-implementaties
- **Operationele Impact**: De auteurs zijn niet verantwoordelijk voor operationele verstoringen
- **Uitgebreide Beveiliging**: Ghost is één onderdeel van een complete beveiligingsstrategie

### Ondersteuning
- **GitHub Issues**: [Rapporteer bugs of vraag functies aan](https://github.com/jimrtyler/Ghost/issues)
- **Documentatie**: Gebruik `Get-Help <functie> -Full` voor gedetailleerde hulp
- **Community**: PowerShell en beveiligingscommunityforums

---

**🔒 Versterk uw beveiligingspositie met Ghost - maar test altijd eerst.**

```powershell
# Begin met beoordeling, niet aannames
Get-Ghost
```

**⭐ Geef deze repository een ster als Ghost helpt bij het verbeteren van uw beveiligingspositie!**