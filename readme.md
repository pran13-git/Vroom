
```markdown
### 🚀 Vroom - One tool to run them all

**Vroom** is a universal project launcher. It detects and runs a wide range of project types automatically — with zero configuration.

---

## 🔧 Installation

### macOS/Linux

```bash
sudo cp vroom /usr/local/bin/
chmod +x /usr/local/bin/vroom
```

**Windows (WSL or Git Bash)**

```bash
cp vroom /usr/local/bin/vroom
chmod +x /usr/local/bin/vroom
```

Ensure `/usr/local/bin/` is in your `$PATH`.

## ⚙️ Usage

```bash
vroom [options]
```

Run in the root directory of your project, or use `--deep` to auto-run all projects recursively.

## 🏃 Basic Commands

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

## 📁 `.vroomrc`

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

## 🧠 Auto Detection Logic

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

## 📦 Auto Dependency Installation

| Language | Package Manager   |
|----------|-------------------|
| Node.js  | `npm`, `yarn`, `pnpm` |
| Python   | `pip`, `poetry`   |
| Rust     | `cargo`           |
| Ruby     | `bundle`          |

## 🌱 Environment Support

* **Virtual Environments:** Activates `.venv`, `venv`, or `env` if present (unless `--notvenv` is passed)
* **.env Files:** Loads `.env` into the environment automatically

## 📋 Examples

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

## 🧪 Tested Platforms

✅ macOS Terminal & iTerm
✅ Linux (Debian, Ubuntu, Arch)
✅ Windows (via WSL2, Git Bash, or IDE terminals like VS Code)

## 💬 FAQ

**Q: Why is it called “Vroom”?**
A: Because it’s fast, fun, and it goes! 💨

**Q: What happens if no project is detected?**
A: You’ll see `❌ Unknown project type.`

**Q: Can I customize the behavior per project?**
A: Yes, just drop a `.vroomrc` in your project root.

## 🛠 Future Ideas

✅ Native Windows `.bat`/.`ps1` support
⏳ Language-specific config overrides
⏳ Plugin system for custom project types

## 🧡 Credits

Built with love by Pranith — for developers who just want to run stuff without thinking.

## 📄 License

MIT
```
