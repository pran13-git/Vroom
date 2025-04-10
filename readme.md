# 🚀 Vroom - One tool to run them all

**Vroom** is a universal project launcher in CLI. It detects and runs a wide range of project types automatically — with zero configuration.

## Why Vroom?
**Vroom** saves time by automatically detecting project types, setting up environments, installing dependencies, and running the right start command — all with a single command. It removes the need to remember how each project works, making it ideal for developers juggling multiple repos, switching between languages, or onboarding into unfamiliar codebases.


## 🔧 Installation

You can install **Vroom** in two ways: via `curl` (recommended for quick install), or by cloning/downloading the project manually.


### Option 1: Quick Install via `curl` (macOS/Linux)

This is the fastest way to get started. It fetches the latest version of `vroom` and makes it executable:

```bash
curl -sSL https://raw.githubusercontent.com/pran13-git/vroom/main/vroom -o /usr/local/bin/vroom && chmod +x /usr/local/bin/vroom
```

✅ This does **not** require cloning the repo.  
✅ You can immediately run `vroom` from any directory.

> Make sure `/usr/local/bin` is in your `$PATH`.

---

### Option 2: Manual Installation (All Platforms)

1. **Download** or **clone** the repository:

```bash
git clone https://github.com/pran13-git/vroom.git
cd vroom
```

2. **Move and make it executable** (macOS/Linux):

```bash
sudo cp vroom /usr/local/bin/
chmod +x /usr/local/bin/vroom
```

3. **For Windows (WSL or Git Bash)**:

```bash
cp vroom /usr/local/bin/vroom
chmod +x /usr/local/bin/vroom
```
> Ensure `/usr/local/bin/` is in your `$PATH`.

## ⚙️ Usage

```bash
vroom [options]
```

Its simple.

## Basic Commands

| Command             | Description                                                     |
|----------------------|-----------------------------------------------------------------|
| `vroom`              | Auto-detect and run the project in the current directory       |
| `vroom --deep`       | Recursively detect and run all projects in subdirectories       |
| `vroom --list`       | List the detected project in the current directory             |
| `vroom --list --deep`| List all detected projects recursively                         |
| `vroom --list --json`| Output list in JSON format                                      |
| `vroom --supported`  | Print all supported project types                             |
| `vroom --log`        | Log output to `vroom.log`                                     |
| `vroom --log=custom.log`| Log output to `custom.log`                                  |
| `vroom --notvenv`    | Skip Python virtual environment auto-activation                |

## `.vroomrc`

Add a `.vroomrc` file to your project root to define a custom startup script. This file will be executed instead of automatic detection.

```bash
#!/bin/bash
echo "Launching my custom setup..."
npm run start:custom
```

Make sure it’s executable:

```bash
chmod +x .vroomrc
```

## Auto Detection Logic

| Project Type | Files Detected                  | Action                                                       |
|--------------|---------------------------------|--------------------------------------------------------------|
| Docker       | `Dockerfile`, `docker-compose.yml` | `docker-compose up` or `docker build && docker run`          |
| Python       | `main.py`, `pyproject.toml`     | `python3 main.py` or `poetry run python main.py`             |
| Node.js      | `package.json`                  | `npm run dev` / `npm start` / `node index.js`               |
| Next.js      | `package.json` with `"next"`      | `npm run dev`                                                |
| React (Vite) | `vite.config.js` / `vite.config.ts`| `npm run dev`                                                |
| Vue.js       | `vue.config.js`                 | `npm run serve`                                              |
| Svelte       | `svelte.config.js`              | `npm run dev`                                                |
| TypeScript   | `tsconfig.json`                 | `ts-node index.ts`                                           |
| Rust         | `Cargo.toml`                    | `cargo run`                                                  |
| Go           | `main.go`                       | `go run main.go`                                             |
| Java         | `Main.java`, `pom.xml`          | `javac Main.java && java Main` or `mvn compile exec:java`    |
| Kotlin       | `build.gradle.kts`              | `./gradlew run`                                              |
| C/C++        | `.c`, `.cpp` files             | `g++ *.cpp -o out && ./out`                                  |
| .NET         | `.csproj`                      | `dotnet run`                                                 |
| PHP          | `index.php`                     | `php index.php`                                              |
| Ruby         | `main.rb`, `Gemfile`            | `ruby main.rb` or `bundle exec ruby main.rb`                |
| Elixir       | `mix.exs`                       | `mix run`                                                    |

## Auto Dependency Installation

| Language | Package Manager   |
|----------|-------------------|
| Node.js  | `npm`, `yarn`, `pnpm` |
| Python   | `pip`, `poetry`   |
| Rust     | `cargo`           |
| Ruby     | `bundle`          |

## Environment Support

* **Virtual Environments:** Activates `.venv`, `venv`, or `env` if present (unless `--notvenv` is passed)
* **.env Files:** Loads `.env` into the environment automatically

## Examples

```bash
vroom
# Runs the project in the current folder

vroom --deep
# Recursively finds and runs every project

vroom --list --json
# Outputs a JSON list of projects

vroom --log
# Logs output to vroom.log

vroom --notvenv
# Skips activating Python venv
```

## Tested Platforms

✅ macOS Terminal  
✅ Linux (Debian, Ubuntu, Arch)  
✅ Windows (via WSL2, Git Bash, or IDE terminals like VS Code)  

## 💬 FAQ

**Q: Why is it called “Vroom”?**
A: Because it’s fast, fun, and it goes! 💨

**Q: What happens if no project is detected?**
A: You’ll see `Unknown project type.`

**Q: Can I customize the behavior per project?**
A: Yes, just drop a `.vroomrc` in your project root.

## Future Ideas

Native Windows support
Extend support for production development

## Credits

Built initially by Pranith ([GitHub](https://github.com/pran13-git), [LinkedIn](https://www.linkedin.com/in/pranith-%E2%80%8E-6673581b7/)) — for developers who just want to run stuff without thinking.

We welcome and appreciate contributions from the open-source community!

## Open Source Contributions

We encourage developers to contribute to Vroom! This can include:

* **Bug fixes:** Identifying and submitting patches for any issues you encounter.
* **New features:** Proposing and implementing new functionalities to enhance Vroom.
* **Improved auto-detection:** Adding support for more project types.
* **Documentation improvements:** Making the documentation clearer and more comprehensive.
* **Testing:** Helping to ensure the stability and reliability of Vroom.
* **Language-specific config overrides:** Contributing to the development of language-specific configurations.
* **Plugin system:** Assisting in the design and implementation of a plugin architecture.
* **Native Windows support:** Contributing to the development of `.bat` and `.ps1` support.

If you'd like to contribute, please:

1.  **Fork the repository** on GitHub.
2.  **Create a new branch** for your contribution.
3.  **Make your changes** and ensure they follow the project's coding style (if any).
4.  **Write clear and concise commit messages.**
5.  **Submit a pull request** with a detailed explanation of your changes.

We will review your contributions and provide feedback. Thank you for helping make Vroom better!

## License

This project is licensed under the GNU General Public License v3.0. The full text of the license is available at [LICENSE](LICENSE).

By contributing to this project, you agree that your contributions will be licensed under the same GNU General Public License v3.0.
