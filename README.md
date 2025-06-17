# Typrr

**Typrr** is a fast, extensible file type detection engine written in Rust.  
It identifies file formats based on magic bytes, headers, MIME types, and deep byte analysis — even when file extensions lie.

> **Know the file. Trust the type.**

---

## 🔍 Features

- 🧬 Detects file types via magic bytes, headers, and signatures
- 🪄 Supports hundreds of formats (DOCX, PDF, PNG, ZIP, EXE, etc.)
- 🧠 Extension-agnostic — identifies files even without an extension
- 📦 Outputs MIME type, format family, and confidence level
- ⚡ Rust-native performance with minimal dependencies
- 🛠️ Embeddable as a library or used as a CLI tool
- 🔌 Pluggable signature system (YAML or JSON-based definitions)

---

## 🚀 Getting Started

### Prerequisites

- Rust (v1.70+)
- Cargo

### Installation

```bash
git clone https://github.com/your-org/typrr.git
cd typrr
cargo build --release
````

---

## 📦 CLI Usage

```bash
typrr detect ./unknown.file
```

**Example Output:**

```json
{
  "file": "unknown.file",
  "mime": "application/pdf",
  "extension": "pdf",
  "format": "PDF",
  "confidence": 0.99
}
```

Scan a folder recursively:

```bash
typrr detect ./uploads --recursive
```

---

## 📚 Library Usage

```rust
use typrr::detect;

let result = detect::from_file("sample.bin")?;
println!("Detected: {}", result.mime_type);
```

---

## 🧩 Supported Detection Modes

* Magic byte matching
* File header analysis
* Container inspection (e.g., ZIP, OLE, TAR)
* Extension fallback (optional)
* Heuristics & confidence scoring

---

## 🔧 Custom Signatures

Define your own signatures via YAML:

```yaml
- name: CustomFormat
  mime: application/x-custom
  header: [0x43, 0x55, 0x53, 0x54] # "CUST"
  offset: 0
  extension: cust
```

Load custom signature sets:

```bash
typrr detect file.cust --signatures ./custom_sigs.yaml
```

---

## 🧪 Testing

```bash
cargo test
```

---

## 🔭 Roadmap

* [ ] Content-aware ZIP/compound detection (e.g., DOCX vs XLSX)
* [ ] Streaming support for large file input
* [ ] Format-specific plugins
* [ ] WebAssembly target

---

## 🤝 Contributing

Pull requests and issues are welcome!
Want to contribute new file format signatures? Start with `signatures/builtins.yaml`.

---

## 📄 License

Licensed under the MIT License.

---

**Typrr** – Trust your type.
