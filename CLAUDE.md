# CLAUDE.md - Project Context for Claude Code

## Project: TYRO Sign Snap
Tiryaki Agro kurumsal e-posta imza oluşturucu. Çalışanlar bu web app ile Outlook imzalarını oluşturur.

## Tech Stack
- React 18 + Vite
- lucide-react@0.263.1 (eski versiyon — Wand2, Sparkles, Building2, Smartphone, PenTool, Trash2, Languages, RotateCcw YOK)
- Güvenli ikonlar: User, Mail, Phone, Globe, MapPin, Clipboard, Check, Settings, Eye, Edit, Edit2, Edit3, Download, ChevronRight, Linkedin, Twitter, Facebook, Instagram, Home, Briefcase, Info, RefreshCw, Sun, Moon, Upload, Image, Trash, Menu, X, Zap, Star, Copy
- Inline styles (CSS-in-JS), no Tailwind, no CSS modules
- Google Fonts: Inter + Plus Jakarta Sans

## Design System (Tiryaki)
- Primary: #1e3a5f (navy)
- Accent: #c8922a (gold)
- Accent Color (divider): #0098d4 (mavi)
- Light theme default, dark mode toggle
- Sidebar fixed left, header fixed top
- TTECH Business Solutions copyright footer in sidebar

## Signature Structure (3 bölüm)
1. SOL: Yüklenen logo (veya fallback text "tiryaki" logosu)
2. ORTA: Dikey accent çizgi ayırıcı + çalışan bilgileri (ad, ünvan, şirket, SDN/Fax, GSM, email, adres)
3. SAĞ: Navy (#1e3a5f) arka planlı blok — sosyal medya ikonları (2x2 grid) + website

## Key Features
- Ofis seçince adres/SDN/Fax otomatik doluyor
- titleCase() fonksiyonu küçük harfle yazılan ünvanları düzeltiyor
- Logo base64 olarak imza HTML'ine gömülüyor
- Kopyalama: document.createRange + execCommand('copy') ile rich HTML
- İndirme: Blob + URL.createObjectURL ile .html dosya

## State Structure
- form: { fullName, titleTR, titleEN, officeId, gsm, email }
- stg (settings): { companyName, website, slogan, logoColor, accentColor, logoBase64, logoW, logoH, social: { linkedin, twitter, facebook, instagram } }

## Offices (hardcoded)
Istanbul, Gaziantep, Mersin, Ankara, Dubai, Moscow, Shanghai

## Important Notes
- Arrow functions (=>) çalışıyor ama artifact ortamında sorun çıkardı, function() tercih edildi
- Object.assign/spread sorun çıkardı, manuel property copy tercih edildi  
- ClipboardItem API desteklenmiyor, DOM-based copy kullanılıyor
- Template literals sorun çıkardı, string concatenation (+) tercih edildi
- Claude Code ortamında bu kısıtlamalar geçerli DEĞİL, modern syntax kullanılabilir

## Folder Structure
```
tyro-sign-snap/
├── index.html
├── package.json
├── vite.config.js
├── README.md
├── CLAUDE.md
├── .gitignore
└── src/
    ├── main.jsx
    └── App.jsx      ← Ana uygulama (tek dosya)
```
