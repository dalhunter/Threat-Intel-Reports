"""
Volt Typhoon Threat Intelligence Report Generator
Enhanced version with better structure and extensibility
"""

from dataclasses import dataclass
from typing import List
from datetime import datetime


@dataclass
class ThreatActor:
    """Represents a threat actor in the intelligence system"""
    name: str
    aliases: List[str]
    origin: str
    affiliation: str
    active_since: str
    threat_level: str


@dataclass
class TargetProfile:
    """Represents target sectors and environments"""
    sectors: List[str]
    geography: str
    criticality: str


class TacticsProcedures:
    """Encapsulates TTPs (Tactics, Techniques, Procedures)"""
    
    def __init__(self):
        self.living_off_land = [
            "PowerShell",
            "WMIC",
            "Netsh",
            "Ntdsutil"
        ]
        self.initial_access = [
            "Weak or default passwords",
            "Unpatched vulnerabilities",
            "Exposed internet-facing systems"
        ]
        self.credential_access = [
            "Credential theft and reuse",
            "Valid login account abuse",
            "Reduced malware reliance"
        ]
        self.persistence_stealth = [
            "Minimal custom malware",
            "Hands-on keyboard activity",
            "Long-term covert presence",
            "Router/VPN compromise"
        ]
    
    def get_all_tactics(self) -> dict:
        """Return all TTPs organized by category"""
        return {
            "Living off the Land": self.living_off_land,
            "Initial Access": self.initial_access,
            "Credential Access": self.credential_access,
            "Persistence & Stealth": self.persistence_stealth
        }


class ThreatIntelligenceReport:
    """Main class for generating threat intelligence reports"""
    
    def __init__(self, actor: ThreatActor, targets: TargetProfile, ttps: TacticsProcedures):
        self.actor = actor
        self.targets = targets
        self.ttps = ttps
        self.generated_at = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    
    def format_section(self, title: str, content: str) -> str:
        """Format a report section with consistent styling"""
        separator = "-" * 50
        return f"\n{separator}\n{title}:\n{separator}\n{content}\n"
    
    def generate_bluf(self) -> str:
        """Generate Bottom Line Up Front summary"""
        bluf = f"{self.actor.name} is a {self.actor.origin}-linked cyber espionage group focused on long-term stealth access to critical infrastructure."
        return self.format_section("BLUF (Bottom Line Up Front)", bluf)
    
    def generate_attribution(self) -> str:
        """Generate attribution section"""
        aliases_str = ", ".join(self.actor.aliases)
        attribution = f"""State-linked: {self.actor.origin}
Believed affiliation: {self.actor.affiliation}
Known aliases: {aliases_str}
Active since: {self.actor.active_since}"""
        return self.format_section("ATTRIBUTION", attribution)
    
    def generate_targets(self) -> str:
        """Generate targets section"""
        sectors = "\n".join(f"• {sector}" for sector in self.targets.sectors)
        targets_info = f"""Primary Sectors:
{sectors}

Geography: {self.targets.geography}
Criticality: {self.targets.criticality}"""
        return self.format_section("TARGETS", targets_info)
    
    def generate_ttps(self) -> str:
        """Generate TTPs section"""
        ttp_content = ""
        for category, techniques in self.ttps.get_all_tactics().items():
            techniques_list = "\n".join(f"  • {t}" for t in techniques)
            ttp_content += f"\n{category}:\n{techniques_list}\n"
        return self.format_section("TACTICS, TECHNIQUES & PROCEDURES", ttp_content)
    
    def generate_threat_assessment(self) -> str:
        """Generate threat assessment section"""
        assessment = f"""Threat Level: {self.actor.threat_level}
Attribution Confidence: High
Detection Difficulty: Very High
Strategic Impact: Critical infrastructure risk"""
        return self.format_section("THREAT ASSESSMENT", assessment)
    
    def generate_report(self) -> str:
        """Compile and generate the complete report"""
        header = "=" * 50
        report = f"""
{header}
THREAT INTELLIGENCE REPORT: {self.actor.name}
Generated: {self.generated_at}
{header}"""
        
        report += self.generate_bluf()
        report += self.generate_attribution()
        report += self.generate_targets()
        report += self.generate_ttps()
        report += self.generate_threat_assessment()
        
        report += f"\n{header}\n"
        return report
    
    def print_report(self) -> None:
        """Print the formatted report to console"""
        print(self.generate_report())
    
    def save_report(self, filename: str) -> None:
        """Save the report to a file"""
        with open(filename, 'w') as f:
            f.write(self.generate_report())
        print(f"Report saved to {filename}")


def main():
    """Main execution function"""
    
    # Define Volt Typhoon threat actor
    volt_typhoon = ThreatActor(
        name="Volt Typhoon",
        aliases=["UNC3236", "VANGUARD PANDA", "Redfly", "VOLTZITE"],
        origin="China",
        affiliation="PLA cyber operations",
        active_since="2021",
        threat_level="HIGH"
    )
    
    # Define target profile
    targets = TargetProfile(
        sectors=[
            "Energy systems",
            "Telecommunications",
            "Transportation networks",
            "Government-adjacent systems"
        ],
        geography="U.S. and Pacific infrastructure (including Guam)",
        criticality="CRITICAL"
    )
    
    # Define TTPs
    ttps = TacticsProcedures()
    
    # Generate and display report
    report = ThreatIntelligenceReport(volt_typhoon, targets, ttps)
    report.print_report()
    
    # Optional: Save report
    # report.save_report("volt_typhoon_report.txt")


if __name__ == "__main__":
    main()
