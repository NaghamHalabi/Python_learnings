# Language History and Comparison

## The Historical Arc

```
1970s  Shell scripts     → "run commands, pipe output"
1977   Awk               → "process text files easily"
1987   Perl              → "awk + shell + more, for sysadmins"
1991   Python            → "perl's power, but readable and structured"
```

Perl was explicitly created because Awk couldn't handle complex tasks and shell was too fragile. Python was created because Perl became unreadable as programs grew.

---

## Quick Comparison

| Aspect              | Shell/Batch               | Awk                        | Perl                      | Python                      |
| ------------------- | ------------------------- | -------------------------- | ------------------------- | --------------------------- |
| **Primary use**     | System automation, glue   | Text processing            | Text processing, sysadmin | General purpose             |
| **Era**             | 1970s (sh), 1980s (batch) | 1977                       | 1987                      | 1991                        |
| **Typing**          | Everything is a string    | Strings + numbers          | Weak, dynamic             | Strong, dynamic             |
| **Data structures** | Basically none            | Arrays, associative arrays | Arrays, hashes, refs      | Lists, dicts, sets, classes |
| **Error handling**  | Exit codes                | Minimal                    | `eval`/`die`              | Exceptions                  |
| **Readability**     | Low (complex scripts)     | Medium (terse)             | Low ("write-only")        | High (explicit design goal) |

---

## Shell/Batch

```bash
# Good at: orchestrating other programs
for f in *.log; do
    gzip "$f"
done
```

**Strengths**: Everywhere, pipes, process control
**Weaknesses**: Quoting hell, no real data structures, error handling is painful

**Use when**: Gluing CLI tools together, simple automation, deployment scripts

### Shell Family Tree

```
1971  sh (Thompson shell)     → original Unix shell
1977  Bourne shell (sh)       → standardized, scripts still work today
1978  csh (C shell)           → C-like syntax, introduced history/aliases
1983  ksh (Korn shell)        → sh + csh features combined
1989  bash (Bourne Again)     → GNU's sh replacement, most common today
1990  zsh                     → bash + more features, macOS default now
```

**Bash = Bourne Again SHell** — the dominant shell on Linux, was macOS default until Catalina (2019).

### Shell vs Batch

| Term  | Platform         | Examples                   |
| ----- | ---------------- | -------------------------- |
| Shell | Unix/Linux/macOS | bash, zsh, sh, fish        |
| Batch | Windows          | `.bat`, `.cmd`, PowerShell |

They serve the same role: automating system tasks, running programs, gluing tools together.

### The Hierarchy

```
Shell scripting (category)
├── bash (Linux default, most common)
├── zsh (macOS default, bash-compatible mostly)
├── sh (POSIX standard, minimal)
└── fish, ksh, etc.

Batch scripting (Windows equivalent)
├── .bat / .cmd (legacy)
└── PowerShell (modern, actually capable)
```

When people say "shell script" in 2026, they usually mean bash unless specified otherwise.

---

## Awk

```awk
# Good at: columnar text processing
{ sum += $3 }
END { print "Total:", sum }
```

**Strengths**: Built for line-by-line text processing, concise for tabular data
**Weaknesses**: Limited scope, no modules, awkward for anything beyond text

**Use when**: Quick log parsing, CSV manipulation, one-liners in shell pipelines

---

## Perl

```perl
# Good at: regex-heavy text munging
while (<>) {
    s/foo/bar/g;
    print if /pattern/;
}
```

**Strengths**: Extremely powerful regex (built into syntax), CPAN ecosystem, flexible
**Weaknesses**: "There's more than one way to do it" → unreadable code, sigil soup (`$@%`)

**Use when**: Legacy systems, regex-heavy transformations, one-off scripts (if you already know it)

---

## Python

```python
# Good at: everything, readably
data = [json.loads(line) for line in open("data.jsonl")]
df = pd.DataFrame(data)
print(df.groupby("category").sum())
```

**Strengths**: Readable, huge ecosystem, scales from scripts to large applications, strong typing optional
**Weaknesses**: Slower than C, GIL limits threading, packaging was historically messy

**Use when**: Almost anything — web, data science, automation, CLI tools, ML

---

## From the Python Tutorial

> "Python is simple to use, but it is a real programming language, offering much more structure and support for large programs than shell scripts or batch files can offer. On the other hand, Python also offers much more error checking than C, and, being a very-high-level language, it has high-level data types built in, such as flexible arrays and dictionaries. Because of its more general data types Python is applicable to a much larger problem domain than Awk or even Perl, yet many things are at least as easy in Python as in those languages."

---

## PHP Developer Perspective

Coming from PHP, Python will feel familiar — both emerged as "better Perl" for different domains (web vs general). The key difference:

- **PHP**: Web-first, request/response model baked in
- **Python**: General-purpose, web is just one library choice!!
