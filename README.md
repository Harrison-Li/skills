# skills

Useful skills I collected

- **Autoresearch:** the skills for iterative optimization of the training procedure for you ML models, adapted from Karpathy's repo <https://github.com/karpathy/autoresearch>
- **HPC connection:** Connect for remote server or HPC
- **codeguideline:** Instruct how LLM write the simplified and clean code without over-decorating, and think twice with carefully examination for wrong modifications.
- **xyzrender-skills:** generate publishable-quality 3D assets for papers with XYZrender
- **pandoc-skills:** Convert between different document formats, such as LaTeX to Word, etc.
- **nature-skills:** Formating like **Nature** journal, copied from <https://github.com/Yuan1z0825/nature-skills>

If you want to create your own skills, you can refers to the  [SKILLS TEMPLATE](skill_temp/README.md)  for standard template construction. Both for **codex** and **Gemini-cli**

## Installation

### 1. Gemini-cli

You can either choose to cd into each individual skill folder to use it, or you can copy the entire 'skills' directory to a location of your choice for convenient access to all skills.
**Clone the repo**

```bash
git clone https://github.com/Harrison-Li/skills.git
cd skills
```

1. Install one skill

```bash
/skills skill_name
```

2. Install all current skills

```bash
for d in skills/*; do
  cp -R "$d" ~/.gemini/skills/
done
```

### 2. Codex

Codex can use these folders directly as local skills. This is the simplest installation path.

**Clone the repo**

```bash
git clone https://github.com/Harrison-Li/skills.git
cd skills
```

**Install one skill**

```bash
mkdir -p ~/.codex/skills
cp -R skills/skill_name ~/.codex/skills/
```

**Install all current skills**

```bash
mkdir -p ~/.codex/skills
for d in skills/*; do
  cp -R "$d" ~/.codex/skills/
done
```
