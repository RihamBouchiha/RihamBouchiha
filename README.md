from pathlib import Path
import shutil
import zipfile

source_dir = Path("/mnt/data/riham-github-profile")
fixed_dir = Path("/mnt/data/riham-github-profile-fixed")

if fixed_dir.exists():
    shutil.rmtree(fixed_dir)

assets_dir = fixed_dir / "assets"
assets_dir.mkdir(parents=True)

# Copy only the reliable PNG assets.
for name in ["hero.png", "stack-map.png", "signature.png"]:
    shutil.copy2(source_dir / "assets" / name, assets_dir / name)

readme = r'''<div align="center">

<img src="./assets/hero.png" width="100%" alt="Riham Bouchiha — Software Engineering and Artificial Intelligence"/>

<br/>

<a href="https://www.rihambouchiha.com/">
  <img src="https://img.shields.io/badge/PORTFOLIO-C95D7B?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio"/>
</a>
<a href="https://www.linkedin.com/in/rihambouchiha">
  <img src="https://img.shields.io/badge/LINKEDIN-916D9C?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>
<a href="mailto:rihambouchiha@ump.ac.ma">
  <img src="https://img.shields.io/badge/EMAIL-D39A4C?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
</a>

</div>

<br/>

## About

I am a **Computer Science Engineering student at ENIAD Berkane**, specialising in **Software Engineering and Artificial Intelligence**.

I enjoy creating complete digital products, from the first interface idea to backend architecture, databases, APIs and deployment. My profile brings together three complementary dimensions:

<table>
<tr>
<td width="33%" valign="top">

### ENGINEERING

Full-stack applications, backend architecture, APIs, databases and scalable systems.

</td>
<td width="33%" valign="top">

### INTELLIGENCE

Machine learning, deep learning, intelligent agents, RAG and useful automation.

</td>
<td width="33%" valign="top">

### EXPERIENCE

Clear interfaces, thoughtful interactions and modern UI/UX designed around real users.

</td>
</tr>
</table>

> I do not want to choose between code, design and intelligence. I want to understand how they work together.

<br/>

## Technical Universe

<img src="./assets/stack-map.png" width="100%" alt="Riham Bouchiha technical stack"/>

<br/>

### Additional foundations

<div align="center">

`Git` · `GitHub` · `VS Code` · `IntelliJ IDEA` · `Postman` · `Trello` · `UML` · `Merise`

`TCP/IP` · `IPv4/IPv6` · `OSI Model` · `DHCP` · `DNS`

</div>

<br/>

## Current Direction

<table>
<tr>
<td width="50%" valign="top">

### Building now

- End-to-end intelligent applications
- Reliable full-stack architectures
- Interfaces that remain simple despite technical complexity
- AI systems grounded in useful context

</td>
<td width="50%" valign="top">

### Growing toward

- Cloud-native and distributed systems
- Advanced DevOps and CI/CD practices
- Production-ready AI agents and RAG pipelines
- Stronger system design and technical ownership

</td>
</tr>
</table>

<br/>

## What drives me

I value **curiosity, clarity and continuous improvement**. Technology changes quickly, so I focus on understanding foundations, experimenting with new approaches and turning what I learn into something practical.

Based in **Morocco** and open to **PFE internships, collaborations and ambitious technical opportunities**.

<br/>

## Connect

<div align="center">

Great ideas often begin with a simple conversation.

<br/><br/>

<a href="https://www.rihambouchiha.com/">
  <img src="https://img.shields.io/badge/EXPLORE_MY_PORTFOLIO-C95D7B?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio"/>
</a>
<a href="https://www.linkedin.com/in/rihambouchiha">
  <img src="https://img.shields.io/badge/CONNECT_ON_LINKEDIN-916D9C?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>
<a href="mailto:rihambouchiha@ump.ac.ma">
  <img src="https://img.shields.io/badge/SEND_AN_EMAIL-D39A4C?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
</a>

<br/><br/>

<img src="./assets/signature.png" width="100%" alt="She codes. She designs. She deploys. And she is only getting started."/>

</div>
'''

(fixed_dir / "README.md").write_text(readme, encoding="utf-8")

instructions = """UPLOAD EXACTLY THIS STRUCTURE TO YOUR GITHUB PROFILE REPOSITORY:

RihamBouchiha/
├── README.md
└── assets/
    ├── hero.png
    ├── stack-map.png
    └── signature.png

IMPORTANT:
1. Upload the whole assets folder, not only README.md.
2. Keep the folder name exactly: assets
3. Keep all filenames lowercase.
4. Place README.md and assets at the repository root.
5. Delete the old SVG files if they are no longer used.
"""
(fixed_dir / "UPLOAD_INSTRUCTIONS.txt").write_text(instructions, encoding="utf-8")

zip_path = Path("/mnt/data/RihamBouchiha-GitHub-Profile-FIXED.zip")
if zip_path.exists():
    zip_path.unlink()

with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as zf:
    for file in fixed_dir.rglob("*"):
        if file.is_file():
            zf.write(file, file.relative_to(fixed_dir))

print(f"Created corrected README: {fixed_dir / 'README.md'}")
print(f"Created complete ZIP: {zip_path}")
print("Files included:")
for file in fixed_dir.rglob("*"):
    if file.is_file():
        print(" -", file.relative_to(fixed_dir))
