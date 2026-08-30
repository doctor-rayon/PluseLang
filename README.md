# Pulse Programming Language ⚡

Pulse is a modern programming language designed with first-class reactive state management (`state` and `watch / when`), an intermediate representation (Pulse IR), a stack-based Virtual Machine (VM), custom binary bytecode (`.pulsec`), and a native Windows executable target (`.exe`).

## Core Features
- **Reactive State (`state`)**: Declare observable state variables (e.g. `state score = 0`).
- **Reactive Observers (`watch / when`)**: Define reaction blocks that execute automatically whenever observed state changes.
- **Cycle Safety**: Native reaction depth limiting preventing infinite state mutation loops.
- **Compiler Pipeline**: Source (`.pulse`) → AST → Pulse IR → Optimizer → Bytecode (`.pulsec`) → Stack VM / Windows PE (`.exe`).
- **Diagnostic Errors**: Detailed error messages with line and column numbers.

---

## CLI Usage

### Check Syntax & Semantics
```bash
pulse check examples/mvp_demo.pulse
```

### Run Pulse Source File
```bash
pulse run examples/mvp_demo.pulse
# Or:
python -m pulse.cli.main run examples/mvp_demo.pulse
```

### Build Binary Bytecode (`.pulsec`)
```bash
pulse build examples/mvp_demo.pulse
# Produces: build/mvp_demo.pulsec
```

### Run Binary Bytecode File (`.pulsec`)
```bash
pulse run build/mvp_demo.pulsec
```

### Build Native Windows Executable (`.exe`)
```bash
pulse build examples/mvp_demo.pulse --target windows
# Produces: dist/mvp_demo.exe
```

### Run Unit Tests
```bash
python -m unittest discover tests
```

---

## Example (`examples/mvp_demo.pulse`)
```pulse
let x = 10
let y = 20

print(x + y)

state score = 0

watch score {
    when score >= 100 => print("Winner")
}

score = 100
```
