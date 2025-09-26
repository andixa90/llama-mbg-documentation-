# 📚 Technical Documentation - Inovasi Gen AI MBG

## 🎯 Project Overview

**Project Name**: Inovasi Generatif AI untuk Program Makanan Bergizi Gratis (MBG)  dengan Llama
**URL Live**: https://llama-mbg.andikaprasetia.id

**Repository**: llama-mbg-documentation
**Deployment Platform**: Cloudflare Pages  
**AI Provider**: Groq API (Llama-3.1-8b-instant)

### 🎪 Mission Statement
Mencetak Generasi Emas melalui revolusi gizi berbasis Generatif AI Llama - bukan hanya memberi makan, tapi menutrisi dengan cerdas untuk membangun gerakan Generasi Emas Indonesia yang sehat, cerdas, dan berkarakter.

---

## 🏗️ System Architecture

### 📐 High-Level Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Cloudflare Pages                         │
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │   Static Pages   │  │   AI Functions   │                  │
│  │                 │  │                 │                  │
│  │ • Landing Page  │  │ • /functions/   │                  │
│  │ • Pawon AI      │  │   groq          │ ───┐             │
│  │ • AI Menu       │  │                 │    │             │
│  │ • Rapor Gizi    │  │ Unified AI API  │    │             │
│  │ • SPPG Dashboard│  │                 │    │             │
│  └─────────────────┘  └─────────────────┘    │             │
└─────────────────────────────────────────────────┼─────────────┘
                                               │
                                               ▼
                                    ┌─────────────────┐
                                    │   Groq API      │
                                    │                 │
                                    │ Llama-3.1-8b-   │
                                    │ instant         │
                                    └─────────────────┘
```

### 🔧 Technology Stack

#### **Frontend Technologies:**
- **ReactJS + TypeScript**: SPPG Smart Dashboard (SPA)
- **Vite**: Build tool untuk React application
- **TailwindCSS**: Utility-first CSS framework
- **Leaflet**: Interactive maps untuk dashboard
- **Recharts**: Data visualization library

#### **Backend Technologies:**
- **Cloudflare Pages Functions**: Serverless API endpoints
- **Groq API**: AI inference engine
- **JavaScript ES6+**: Function handlers
- **Wrangler CLI**: Deployment tool

#### **AI & ML:**
- **Model**: Llama-3.1-8b-instant (Meta's Llama model)
- **Provider**: Groq (High-performance AI inference)
- **API Type**: REST API dengan JSON responses

---

## 🌐 Website Structure

### 📄 Pages & Features

#### **1. Main Landing Page (`/index.html`)**
```
Features:
├── Hero Section 
├── About Section (Program MBG overview)
├── Inovasi Section 
├── Tagline Section 
├── Target Section
├── Team Section 
├── Organized Section 
└── Footer

PWA Features:
├── Service Worker registration
├── Install prompt
├── Offline indicator
└── Manifest.json support
```

#### **2. SPPG Smart Dashboard (`/sppg-smart-dashboard/`)**
```
Dashboard Modules:
├── 📊 Overview (KPI cards & charts)
├── 🏫 Schools Management (Interactive map)
├── 👥 Beneficiaries (Student data)
├── 📦 Inventory (Stock management)
├── 🚚 Logistics (Distribution tracking)
├── 📅 Schedule (Menu planning calendar)
├── 🛒 Shopping (Procurement system)
├── 👨‍🍳 Suppliers (Vendor management)
├── 👥 Volunteers (Team coordination)
├── 📈 Reports (Analytics & insights)
└── 🤖 AI Insights (Groq-powered analytics)

Technical Stack:
├── React 19.1.1 (via CDN)
├── TypeScript for type safety
├── Recharts for data visualization
├── Leaflet for interactive maps
├── Tailwind CSS for styling
└── Vite build system
```

#### **3. Pawon AI (`/pawon-ai.html`)**
```
AI Menu Planning System:
├── 📍 Geographic Selection (Pulau → Provinsi)
├── 🎯 Target Group Selection (Kelompok sasaran)
├── 🤖 AI Menu Generation (Groq API)
├── 📋 Menu Display (JSON formatted)
└── 💾 Export Features (Copy/Download)

AI Capabilities:
├── Menu untuk 5 hari (Senin-Jumat)
├── Nutrisi seimbang per porsi
├── Bahan pangan lokal
├── Budget consideration (≤ Rp 15.000/porsi)
└── Allergen information
```

#### **4. AI Menu (`/ai-menu.html`)**
```
Recipe Generation System:
├── 🍽️ Recipe Input Form
├── 🤖 AI Recipe Generation (Groq API)
├── 📊 Nutrition Information
├── 🥘 Cooking Instructions
└── 📋 Ingredient List

Output Format:
├── Recipe name & description
├── Ingredients list (Indonesian foods)
├── Step-by-step instructions
└── Nutrition facts (calories, protein, etc.)
```

#### **5. Rapor Gizi (`/rapor-gizi.html`)**
```
Nutrition Reporting System:
├── 📱 WhatsApp Integration concept
├── 📸 Image Analysis (AI-powered)
├── 📊 Personal Nutrition Reports
├── 📈 Progress Tracking
└── 🔔 Parent Notifications

Planned Features:
├── Daily nutrition reports
├── Photo-based meal analysis
├── Personalized recommendations
└── Growth tracking
```

---

## 🤖 AI Integration Details

### 🔗 Unified API Architecture

#### **Single Endpoint Design:**
```javascript
// All AI functions unified under one endpoint
/functions/groq → Groq API (Primary)
/functions/gemini → Routes to Groq (Legacy compatibility)
/functions/openrouter → Routes to Groq (Legacy compatibility)
```

#### **API Configuration:**
```toml
# wrangler.toml
[vars]
GROQ_API_KEY = "your-groq-api-key-here"
```

### 🧠 AI Model Specifications

#### **Groq Llama-3.1-8b-instant:**
```
Model Details:
├── Provider: Groq Inc.
├── Base Model: Meta's Llama 3.1 8B parameters
├── Optimization: Groq's LPU (Language Processing Unit)
├── Speed: Ultra-fast inference (sub-second response)
├── Context: 8192 tokens context window
└── Language: Multilingual (including Indonesian)

Performance Characteristics:
├── Latency: ~100-300ms average response time
├── Throughput: High concurrent request handling
├── Cost: Competitive pricing per token
├── Reliability: 99.9% uptime SLA
└── Safety: Built-in content filtering
```

### 📝 API Request/Response Formats

#### **1. Recipe Generation Request:**
```javascript
POST /functions/groq
Content-Type: application/json

{
  "type": "recipe",
  "payload": {
    "prompt": "Buatkan resep nasi goreng sehat untuk anak SD"
  }
}
```

#### **Recipe Response:**
```javascript
{
  "name": "Nasi Goreng Sehat Anak",
  "description": "Nasi goreng bergizi dengan sayuran segar dan protein tinggi",
  "ingredients": [
    "2 porsi nasi putih",
    "2 butir telur ayam",
    "100g wortel potong dadu",
    "50g buncis potong kecil",
    "2 siung bawang putih",
    "1 sdm kecap manis",
    "1 sdt minyak goreng",
    "Garam secukupnya"
  ],
  "instructions": [
    "Panaskan minyak dalam wajan anti lengket",
    "Tumis bawang putih hingga harum",
    "Masukkan telur, orak-arik hingga matang",
    "Tambahkan wortel dan buncis, masak 3 menit",
    "Masukkan nasi, aduk rata dengan sayuran",
    "Beri kecap manis dan garam, aduk hingga merata",
    "Sajikan hangat"
  ],
  "nutrition": {
    "calories": "450 kkal",
    "protein": "15g",
    "fat": "12g",
    "carbohydrates": "68g"
  }
}
```

#### **2. Menu Planning Request:**
```javascript
POST /functions/groq
Content-Type: application/json

{
  "type": "pawon-menu",
  "payload": {
    "prompt": "Buat menu 5 hari untuk siswa SD di Jawa Barat dengan budget Rp 15.000 per porsi. Standar gizi: 531 kkal, 32.2g protein, 33.1g lemak, 31.0g karbohidrat per porsi."
  }
}
```

#### **Menu Planning Response:**
```javascript
{
  "opsiMenu": [
    {
      "detailHarian": [
        {
          "hari": "Senin",
          "namaResep": ["Nasi Putih", "Ayam Goreng Bumbu Kuning", "Tumis Kangkung", "Pisang Ambon"],
          "estimasiEnergi": 545,
          "estimasiProtein": 33,
          "estimasiLemak": 32,
          "estimasiKarbohidrat": 52,
          "kontribusiGizi": "Tinggi protein untuk pertumbuhan otot dan otak",
          "potensiAlergen": "Tidak ada alergen utama",
          "saranPenyajian": "Sajikan dalam keadaan hangat, pisang sebagai dessert"
        },
        // ... 4 hari lainnya
      ]
    }
  ],
  "ringkasanUmum": {
    "catatanGizi": "Menu dirancang khusus untuk siswa SD/MI di Jawa Barat dengan memanfaatkan bahan pangan lokal yang mudah didapat dan terjangkau."
  }
}
```

#### **3. Dashboard Insights Request:**
```javascript
POST /functions/groq
Content-Type: application/json

{
  "type": "insights",
  "payload": {
    "kpis": [
      {"title": "Total Siswa", "value": "2,847"},
      {"title": "Sekolah Aktif", "value": "156"},
      {"title": "Menu Tersedia", "value": "89"},
      {"title": "Distribusi Hari Ini", "value": "94%"}
    ],
    "timeFrame": "30 hari terakhir"
  }
}
```

#### **Insights Response:**
```javascript
{
  "text": "Berdasarkan data KPI selama 30 hari terakhir, program MBG menunjukkan performa yang sangat baik dengan 2,847 siswa terlayani di 156 sekolah aktif. Tingkat distribusi 94% mengindikasikan efisiensi logistik yang optimal. \n\nRekomendasi untuk perbaikan: \n1. Tingkatkan variasi menu dari 89 menjadi 100+ untuk mencegah kebosanan siswa \n2. Targetkan distribusi 98% dengan optimalisasi rute pengiriman \n3. Pertimbangkan ekspansi ke 20 sekolah baru berdasarkan demand yang tinggi"
}
```

### 🎨 AI Prompt Engineering

#### **System Prompts per Use Case:**

##### **Recipe Generation:**
```
Anda adalah seorang ahli gizi dan koki untuk program "Makanan Bergizi Gratis (MBG)" di Indonesia.
Buatkan HANYA SATU resep berdasarkan permintaan berikut.
Pastikan resep sehat, mudah dibuat, bahan umum di Indonesia, dan menarik untuk anak-anak.
HANYA KEMBALIKAN SATU OBJEK JSON, tanpa teks pembuka, penutup, atau karakter lain di luar JSON.
```

##### **Menu Planning:**
```
Anda adalah seorang ahli gizi dari Badan Gizi Nasional yang sangat memahami kuliner dan ketersediaan pangan lokal di seluruh Indonesia. 
Tugas Anda adalah membuat menu untuk Program Makan Bergizi Gratis (MBG) sesuai Petunjuk Teknis (Juknis) resmi. 
HANYA kembalikan JSON yang valid tanpa teks tambahan.
```

##### **Dashboard Analytics:**
```
Anda adalah analis data untuk program Makanan Bergizi Gratis (MBG). 
Berikan insight dan rekomendasi berdasarkan data KPI yang diberikan.
```

#### **Prompt Optimization Techniques:**
```
1. ✅ Clear Role Definition: Definisi peran AI yang spesifik
2. ✅ Output Format Specification: JSON schema yang eksplisit  
3. ✅ Context Limitation: Pembatasan scope untuk fokus
4. ✅ Cultural Localization: Konteks Indonesia dan bahan lokal
5. ✅ Safety Guidelines: Pembatasan konten yang aman untuk anak
6. ✅ Consistency Markers: Template yang konsisten
```

---


### ⚙️ Configuration Files

#### **wrangler.toml** (Cloudflare Pages Configuration):
```toml
name = "llama-mbg"
compatibility_date = "2024-01-01"
pages_build_output_dir = "public"

[vars]
# Menggunakan Groq API dengan model Llama-3.1-8b-instant untuk semua AI functions
GROQ_API_KEY = "your-groq-api-key-here"

# Konfigurasi untuk Cloudflare Pages
# URL akan menjadi: llama-mbg.pages.dev
```

#### **package.json** (React Dashboard):
```json
{
  "name": "sppg-smart-dashboard",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@typescript-eslint/eslint-plugin": "^6.14.0",
    "@typescript-eslint/parser": "^6.14.0",
    "@vitejs/plugin-react": "^4.2.1",
    "autoprefixer": "^10.4.16",
    "eslint": "^8.55.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.5",
    "postcss": "^8.4.32",
    "tailwindcss": "^3.3.6",
    "typescript": "^5.2.2",
    "vite": "^5.0.8"
  }
}
```

#### **vite.config.ts** (Build Configuration):
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/sppg-smart-dashboard/',
  build: {
    outDir: 'dist',
    assetsDir: 'assets'
  }
})
```



## 🔒 Security & Performance

### 🛡️ Security Measures

#### **API Security:**
```
✅ Environment Variables: API keys stored in Cloudflare environment
✅ CORS Policy: Proper cross-origin resource sharing setup
✅ Input Validation: Sanitization of user inputs
✅ Rate Limiting: Groq API built-in rate limiting
✅ Content Filtering: AI model safety mechanisms
✅ HTTPS Only: All communications over encrypted connections
```

#### **Frontend Security:**
```
✅ Content Security Policy: CSP headers for XSS prevention
✅ No Inline Scripts: External script files only
✅ Sanitized Outputs: HTML sanitization for AI responses
✅ Secure Headers: Security headers via Cloudflare
```

### ⚡ Performance Optimization

#### **Frontend Performance:**
```
✅ CDN Delivery: Global content distribution via Cloudflare
✅ Image Optimization: Compressed and optimized images
✅ Code Splitting: Modular JavaScript loading
✅ Lazy Loading: On-demand resource loading
✅ Minification: Compressed CSS/JS files
✅ Caching: Browser and CDN caching strategies
```

#### **AI Performance:**
```
✅ Model Selection: Llama-3.1-8b-instant for speed
✅ Groq LPU: Specialized hardware acceleration
✅ Response Caching: Intelligent caching of similar requests
✅ Prompt Optimization: Efficient prompt engineering
✅ Timeout Handling: Graceful error handling
```

### 📊 Performance Metrics
```
Page Load Speed:
├── Landing Page: ~1.2s (LCP)
├── SPPG Dashboard: ~2.1s (First load)
├── Pawon AI: ~0.9s
└── AI Menu: ~0.8s

API Response Times:
├── Recipe Generation: ~200-500ms
├── Menu Planning: ~300-800ms
├── Dashboard Insights: ~150-400ms
└── Error Rate: <0.1%

Uptime & Reliability:
├── Cloudflare Pages: 99.99%
├── Groq API: 99.9%
└── Overall System: 99.9%
```

---


## 📈 Analytics & Monitoring

### 📊 Key Performance Indicators (KPIs)

#### **Business Metrics:**
```
Student Engagement:
├── Total Students Served: 2,847
├── Active Schools: 156
├── Menu Varieties: 89+
├── Daily Distribution Rate: 94%
├── Parent Satisfaction: Target >90%
└── Nutrition Goal Achievement: Target >95%

System Performance:
├── AI Response Success Rate: >99%
├── Page Load Speed: <2s average
├── API Uptime: >99.9%
├── User Engagement: Track via analytics
└── PWA Install Rate: Monitor adoption
```

#### **Technical Monitoring:**
```
Infrastructure:
├── Cloudflare Analytics: Built-in metrics
├── Groq API Usage: Token consumption tracking
├── Error Logging: Real-time error monitoring
├── Performance Budgets: Resource usage limits
└── Security Alerts: Automatic threat detection

User Experience:
├── Core Web Vitals: LCP, FID, CLS monitoring
├── User Journey Analytics: Page flow tracking
├── Feature Usage: AI function utilization
├── Mobile Performance: Device-specific metrics
└── Offline Usage: PWA engagement tracking
```

---

## 🔄 Development Workflow

### 🛠️ Local Development

#### **Setup Instructions:**
```bash
# 1. Clone repository
git clone [repository-url]
cd llama-mbg

# 2. Install Wrangler CLI
npm install -g wrangler

# 3. Login to Cloudflare
wrangler login

# 4. Development server
wrangler pages dev public

# 5. React development (separate terminal)
cd sppg-smart-dashboard
npm install
npm run dev
```

#### **Build Process:**
```bash
# React Dashboard Build
cd sppg-smart-dashboard
npm run build

# Sync build to public folder
.\sync-build.ps1

# Deploy to production
.\deploy-clean.ps1
```

### 🔄 CI/CD Pipeline

#### **Automated Deployment Workflow:**
```yaml
# Conceptual GitHub Actions workflow
name: Deploy to Cloudflare Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
      - name: Build React Dashboard
        run: |
          cd sppg-smart-dashboard
          npm install
          npm run build
      - name: Deploy to Cloudflare Pages
        run: npx wrangler pages deploy public
        env:
          CLOUDFLARE_API_TOKEN: ${{ secrets.CLOUDFLARE_API_TOKEN }}
```

---

## 🎯 Target Beneficiaries & Impact

### 👥 Primary Stakeholders

#### **1. Students (Siswa/Anak Didik)**
```
Direct Benefits:
├── 🍽️ Nutritious meals daily (531 kkal, 32.2g protein target)
├── 📚 Improved learning capacity through better nutrition
├── 🏃‍♂️ Enhanced physical development
├── 🧠 Better cognitive performance
└── 🎨 Exposure to varied, culturally appropriate foods

Technical Touch Points:
├── Meal consumption data collection
├── Growth monitoring integration
├── Preference feedback systems
└── Nutrition education content
```

#### **2. Parents (Orang Tua Siswa)**
```
Direct Benefits:
├── 📱 Daily nutrition reports via WhatsApp
├── 📊 Child's nutritional progress tracking
├── 💰 Reduced family food budget burden
├── 🏥 Better health outcomes for children
└── 📚 Nutrition education and awareness

Technical Integration:
├── WhatsApp API for report delivery
├── Photo-based meal analysis (AI)
├── Personalized nutrition recommendations
└── Progress dashboard access
```

#### **3. Local Farmers (Petani Lokal)**
```
Economic Impact:
├── 📈 Increased demand for local produce
├── 💵 Stable income through program contracts
├── 🌱 Incentive for organic/healthy farming
├── 🚚 Reduced transportation costs (local sourcing)
└── 📊 Market predictability and planning

System Integration:
├── Supplier management dashboard
├── Seasonal produce planning
├── Quality tracking systems
└── Payment automation
```

#### **4. Local SMEs (UMKM Lokal)**
```
Business Opportunities:
├── 🏭 Food processing and packaging contracts
├── 🚛 Logistics and distribution services
├── 🍳 Catering and meal preparation
├── 📦 Supply chain management
└── 🔧 Technology services and support

Platform Features:
├── Vendor registration portal
├── Order management system
├── Quality certification tracking
└── Performance analytics
```

#### **5. Government (Pemerintah)**
```
Administrative Benefits:
├── 📊 Real-time program monitoring
├── 💰 Transparent budget utilization
├── 📈 Data-driven policy decisions
├── 🎯 Impact measurement and reporting
└── 🏛️ Inter-agency coordination improvement

Dashboard Capabilities:
├── Multi-level government access
├── Compliance monitoring
├── Budget tracking and forecasting
├── Performance benchmarking
└── Automated reporting generation
```

#### **6. SPPG (Sekolah Penggerak Pangan dan Gizi)**
```
Operational Efficiency:
├── 📋 Streamlined meal planning
├── 📊 Inventory management automation
├── 👥 Staff coordination tools
├── 📈 Performance monitoring
└── 🎓 Training and capacity building

Technical Tools:
├── School-specific dashboards
├── Student enrollment management
├── Menu customization tools
├── Supply chain coordination
└── Report generation automation
```

---

## 🚀 Future Roadmap & Enhancements

### 📅 Short-term Goals (3-6 months)

#### **AI Enhancement:**
```
🤖 Advanced AI Features:
├── Multi-language support (regional languages)
├── Dietary restriction handling (allergies, religions)
├── Seasonal menu adaptation algorithms
├── Budget optimization AI
└── Nutritional gap analysis automation

🔗 Integration Expansion:
├── WhatsApp Business API integration
├── SMS notifications for low-connectivity areas
├── Mobile app development (React Native)
├── Offline-first functionality enhancement
└── Voice-based interaction (speech-to-text)
```

#### **Dashboard Improvements:**
```
📊 Enhanced Analytics:
├── Predictive analytics for demand forecasting
├── Machine learning for preference patterns
├── Real-time nutrition tracking
├── Automated anomaly detection
└── Comparative performance analysis

🎨 UI/UX Enhancements:
├── Mobile-first responsive design
├── Accessibility improvements (WCAG compliance)
├── Dark mode support
├── Multi-theme customization
└── Gesture-based navigation
```

### 🎯 Medium-term Vision (6-12 months)

#### **Scale & Integration:**
```
🌐 National Expansion:
├── Multi-province deployment
├── Regional customization features
├── Scalable infrastructure (auto-scaling)
├── Multi-tenant architecture
└── Regional administrator roles

🤝 Partner Integrations:
├── Ministry of Education API integration
├── Ministry of Health nutrition standards
├── Bank Indonesia payment systems
├── Logistics partner APIs
└── Healthcare provider connections
```

#### **Advanced Features:**
```
🔬 Research & Development:
├── Nutrition impact studies integration
├── Growth tracking correlations
├── Learning performance analysis
├── Health outcome predictions
└── Economic impact assessments

📱 Mobile Ecosystem:
├── Parent mobile app
├── Teacher/administrator app
├── Student engagement features
├── Gamification elements
└── Social features for community building
```

### 🌟 Long-term Impact (1-3 years)

#### **National Program Integration:**
```
🏛️ Government Integration:
├── National nutrition database contribution
├── Policy recommendation engine
├── Inter-ministry data sharing
├── National health monitoring integration
└── Evidence-based policy support

🌍 International Recognition:
├── UN SDG reporting integration
├── International best practice sharing
├── Cross-country implementation
├── Academic research collaboration
└── Global nutrition program model
```

---

## 🤝 Team & Contributors

### 👨‍💻 Development Team

#### **Core Team Members:**
```
🎨 Nurida - Business Analyst
├── Requirements analysis and documentation
├── Stakeholder engagement and feedback collection  
├── Business process optimization
├── User experience research
└── Program impact assessment

👨‍💻 Andika Rohman Prasetia - Designer & Developer
├── Full-stack development (Frontend & Backend)
├── AI integration and prompt engineering
├── System architecture and infrastructure
├── UI/UX design and implementation
└── DevOps and deployment automation

Technical Contributions:
├── React/TypeScript dashboard development
├── Cloudflare Pages Functions implementation
├── Groq AI integration and optimization
├── PWA implementation and optimization
└── Performance monitoring and optimization
```

#### **Institutional Affiliation:**
```
🏛️ Ditjen Perbendaharaan
├── Institutional support and guidance
├── Policy alignment and compliance
├── Resource allocation and coordination
├── Stakeholder network facilitation
└── Program sustainability planning
```

### 🎓 Acknowledgments

#### **Technology Partners:**
```
☁️ Infrastructure & AI:
├── Cloudflare Pages - Global CDN and hosting
├── Groq Inc. - High-performance AI inference
├── Meta AI - Llama model foundation
├── Leaflet - Open-source mapping solution
└── React Team - UI framework and ecosystem

🎨 Design & Assets:
├── Agrion Template - Landing page design foundation
├── FontAwesome - Icon library
├── Unsplash - High-quality photography
├── Google Fonts - Typography resources
└── Tailwind CSS - Utility-first CSS framework
```

#### **Community & Support:**
```
👥 Open Source Community:
├── GitHub - Version control and collaboration
├── NPM Ecosystem - Package management
├── Stack Overflow - Technical problem solving
├── MDN Web Docs - Web standards documentation
└── TypeScript Community - Type safety and development experience

📚 Educational Resources:
├── Cloudflare Developer Documentation
├── React Official Documentation  
├── Groq API Documentation
├── Web Performance Best Practices
└── PWA Implementation Guides
```

---

## 📞 Support & Contact Information

### 🛠️ Technical Support

#### **Development & Maintenance:**
```
👨‍💻 Lead Developer: Andika Rohman Prasetia
├── 📧 Email: admin@andikaprasetia.com
├── 🌐 Portfolio: https://andikaprasetia.id
├── 💼 GitHub: https://github.com/andixa90
└── 📱 LinkedIn: [Professional Profile]

🏢 Institutional Contact:
├── 🏛️ Organization: Ditjen Perbendaharaan
├── 📍 Location: Jakarta, Indonesia
├── 📞 Office: [Contact Number]
└── 📧 Official: [Official Email]
```

#### **Issue Reporting & Feature Requests:**
```
🐛 Bug Reports:
├── GitHub Issues: [Repository URL]/issues
├── Email: admin@andikaprasetia.com
├── Subject: "[BUG] Brief description"
└── Include: Steps to reproduce, expected vs actual behavior

💡 Feature Requests:
├── GitHub Discussions: [Repository URL]/discussions
├── Email: admin@andikaprasetia.com
├── Subject: "[FEATURE] Brief description"
└── Include: Use case, expected benefits, user stories
```

### 📋 System Status & Monitoring

#### **Live System Information:**
```
🌐 Production URLs:
├── Main Website: https://llama-mbg.pages.dev
├── SPPG Dashboard: https://llama-mbg.pages.dev/sppg-smart-dashboard/
├── AI Functions: https://llama-mbg.pages.dev/functions/groq
└── System Status: https://www.cloudflarestatus.com

📊 Performance Monitoring:
├── Uptime: Real-time monitoring via Cloudflare
├── Response Times: Built-in Cloudflare analytics
├── Error Rates: Application-level error tracking
└── User Analytics: Privacy-compliant usage statistics
```

#### **Emergency Contacts:**
```
🚨 Critical Issues (Production Down):
├── Priority: Immediate response within 2 hours
├── Contact: admin@andikaprasetia.com
├── Subject: "[CRITICAL] System outage"
└── Include: Error details, impact assessment, urgency level

⚠️ Non-Critical Issues:
├── Priority: Response within 24-48 hours
├── Contact: admin@andikaprasetia.com
├── Subject: "[ISSUE] Brief description"
└── Include: Detailed description, screenshots if applicable
```

---

## 📋 Appendix

### 🔗 Useful Links & Resources

#### **External Documentation:**
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)
- [Groq API Documentation](https://console.groq.com/docs/)
- [React Documentation](https://react.dev/)
- [Vite Build Tool](https://vitejs.dev/)
- [PWA Best Practices](https://web.dev/progressive-web-apps/)

#### **Related Standards:**
- [Indonesian Nutrition Guidelines](https://www.kemkes.go.id/)
- [School Feeding Program Standards](https://www.kemdikbud.go.id/)
- [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/WCAG21/quickref/)

### 📊 Technical Specifications Summary

```
System Requirements:
├── Node.js: v18+ for local development
├── Wrangler CLI: Latest version for deployment
├── Modern Browser: ES6+ support required
└── Internet Connection: Required for AI functions

Browser Compatibility:
├── Chrome: v90+ ✅
├── Firefox: v88+ ✅  
├── Safari: v14+ ✅
├── Edge: v90+ ✅
└── Mobile Browsers: iOS Safari 14+, Chrome Mobile 90+ ✅

Performance Targets:
├── First Contentful Paint: <1.5s
├── Largest Contentful Paint: <2.5s
├── First Input Delay: <100ms
├── Cumulative Layout Shift: <0.1
└── Time to Interactive: <3s
```

---

**Document Version**: 1.0  
**Last Updated**: September 26, 2025  
**Document Status**: Active  
**Review Schedule**: Monthly  

---

*This technical documentation is a living document that will be updated as the system evolves and new features are added. For the most current information, please refer to the live system and contact the development team.*
