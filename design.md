# TimelineTasks Design System — "Playful Planning"

Denne fil definerer den visuelle retning for TimelineTasks.
Designet skal vaere **legende, varmt og indbydende** — ikke corporate.
Brugerne planlagger livets store oejeblikke; designet skal foeles som en ven, ikke et regneark.

---

## 1. Design-principper

| Princip | Betydning |
|---|---|
| **Varmt, ikke sterilt** | Brug bloede farver, runde former og venlig typografi. Ingen skarpe kanter eller kold graa. |
| **Legende, ikke userioes** | Micro-animationer, emojis og illustrationer giver personlighed — men layoutet forbliver rent og laesbart. |
| **Foelelsesdrevet** | Hvert element skal fremkalde en foelelse: tryghed, glaede, overskuelighed. Kopitekst er opmutrende, aldrig teknisk. |
| **Mobil-foerst** | Alt designes til 375px foerst, skalerer op. Touch-targets minimum 44x44px. |

---

## 2. Farvepalet

### Primaerfarver
| Navn | Hex | Brug |
|---|---|---|
| **Coral** | `#FF6B6B` | Primaer CTA, fremhaevelser, primaer gradient-start |
| **Warm Purple** | `#845EC2` | Gradient-slut, sekundaer accent, links |
| **Soft Peach** | `#FFF5F0` | Baggrund, hero-sektioner |

### Sekundaerfarver
| Navn | Hex | Brug |
|---|---|---|
| **Sunshine** | `#FFD93D` | Badges, highlights, opmuntring |
| **Mint** | `#6BCB77` | Success, completed-states, progress |
| **Sky** | `#4D96FF` | Informations-badges, links |
| **Blush** | `#FEC5E5` | Bagelementer, blobber, dekorative former |

### Neutraler
| Navn | Hex | Brug |
|---|---|---|
| **Charcoal** | `#2D3436` | Overskrifter, primaer tekst |
| **Warm Grey** | `#636E72` | Sekundaer tekst, labels |
| **Cloud** | `#F8F9FA` | Card-baggrunde |
| **Mist** | `#E9ECEF` | Dividers, borders |

### Gradienter
```css
/* Primaer CTA-gradient */
background: linear-gradient(135deg, #FF6B6B 0%, #845EC2 100%);

/* Bagelement-gradient (hero-sektioner) */
background: linear-gradient(180deg, #FFF5F0 0%, #FFFFFF 100%);

/* Variant A (Wedding): varm og romantisk */
background: linear-gradient(135deg, #FEC5E5 0%, #FFF5F0 50%, #E8D5F5 100%);

/* Variant B (Vacation): frisk og livlig */
background: linear-gradient(135deg, #C9F0FF 0%, #FFF5F0 50%, #FFE8CC 100%);
```

---

## 3. Typografi

### Font: **Nunito** (Google Fonts)
Rund, venlig sans-serif der foeles uformel og letlaeselig.

```css
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap');

font-family: 'Nunito', -apple-system, BlinkMacSystemFont, sans-serif;
```

| Element | Vaegt | Stoerrelse | Linjehojde |
|---|---|---|---|
| **Hero headline** | 800 (ExtraBold) | 36px / 2.25rem | 1.2 |
| **Sektionsoverskrift** | 700 (Bold) | 22px / 1.375rem | 1.3 |
| **Card headline** | 700 | 16px / 1rem | 1.4 |
| **Body tekst** | 400 (Regular) | 15px / 0.9375rem | 1.6 |
| **Subtext / labels** | 600 (SemiBold) | 12px / 0.75rem | 1.5 |
| **CTA-knapper** | 700 | 16px / 1rem | 1 |

---

## 4. Former og Afrunding

| Element | Border-radius |
|---|---|
| **Knapper** | `16px` (pilleformet) |
| **Cards** | `20px` |
| **Badges** | `999px` (fuld pille) |
| **Avatarer** | `50%` (cirkel) |
| **Inputfelter** | `12px` |
| **Modaler** | `24px 24px 0 0` (bund-sheet) |

### Dekorative Blob-former
Brug SVG-blobber som baggrundselementer til at bryde det firkantede layout:

```css
/* Eksempel: flydende blob i hero */
.blob {
  position: absolute;
  border-radius: 50% 40% 60% 30% / 40% 50% 30% 60%;
  opacity: 0.15;
  animation: float 8s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  33% { transform: translate(15px, -20px) rotate(5deg); }
  66% { transform: translate(-10px, 10px) rotate(-3deg); }
}
```

---

## 5. Skygger

Bloede, varme skygger — aldrig skarpe eller mork-graa:

```css
/* Card-skygge */
box-shadow: 0 4px 20px rgba(132, 94, 194, 0.08);

/* Hover-skygge */
box-shadow: 0 8px 30px rgba(132, 94, 194, 0.15);

/* CTA-knap-skygge */
box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
```

---

## 6. Animationer og Micro-interaktioner

### Principper
- Alle animationer er **snappy** (200-400ms)
- Easing: `cubic-bezier(0.34, 1.56, 0.64, 1)` (let bounce)
- Ingen animation blokerer interaktion
- Respekter `prefers-reduced-motion`

### Standard-animationer
```css
/* Bounce-in for cards og elementer */
@keyframes bounceIn {
  0% { transform: scale(0.9); opacity: 0; }
  60% { transform: scale(1.02); }
  100% { transform: scale(1); opacity: 1; }
}

/* Slide-up for modaler og sektioner */
@keyframes slideUp {
  from { transform: translateY(30px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

/* Pulse for CTA-knapper */
@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.03); }
}

/* Knap hover */
.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 107, 107, 0.35);
}
```

### Carousel-animation
```css
/* Fade + slide for carousel-overgang */
.carousel-slide {
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.carousel-slide.entering { opacity: 0; transform: translateX(40px); }
.carousel-slide.active { opacity: 1; transform: translateX(0); }
.carousel-slide.leaving { opacity: 0; transform: translateX(-40px); }
```

---

## 7. Ikoner og Emojis

### Emoji som primaere ikoner
Brug native emojis som feature-ikoner — de er universelle, farverige og legendariske.

| Kontekst | Emoji |
|---|---|
| Bryllup | &#x1F492; &#x1F490; &#x1F48D; &#x2764;&#xFE0F; |
| Ferie | &#x2708;&#xFE0F; &#x1F3D6;&#xFE0F; &#x1F9F3; &#x1F30D; |
| Opgave faerdig | &#x1F389; &#x2705; &#x1F31F; |
| Tidslinje | &#x1F4C5; &#x23F0; &#x1F4CB; |
| Milestone | &#x1F3AF; &#x1F680; &#x2B50; |

### Supplerende SVG-ikoner
Til navigation og UI-kontroller brug Lucide icons (stroke-width: 2, runde line-caps).

---

## 8. Komponent-specifikationer

### Primaer CTA-knap
```css
.cta-primary {
  background: linear-gradient(135deg, #FF6B6B, #845EC2);
  color: white;
  font-weight: 700;
  font-size: 16px;
  padding: 16px 32px;
  border-radius: 16px;
  border: none;
  box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
  transition: all 0.2s cubic-bezier(0.34, 1.56, 0.64, 1);
}
.cta-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 25px rgba(255, 107, 107, 0.4);
}
```

### Carousel Card (Landing Pages)
```css
.carousel-card {
  background: white;
  border-radius: 20px;
  padding: 24px;
  box-shadow: 0 4px 20px rgba(132, 94, 194, 0.08);
  max-width: 320px;
  margin: 0 auto;
}
```

### Dot-indikator (Carousel)
```css
.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #E9ECEF;
  transition: all 0.3s ease;
}
.dot.active {
  width: 28px;
  border-radius: 5px;
  background: linear-gradient(135deg, #FF6B6B, #845EC2);
}
```

### Email Signup-felt
```css
.email-group {
  display: flex;
  gap: 8px;
  max-width: 420px;
}
.email-input {
  flex: 1;
  padding: 14px 18px;
  border: 2px solid #E9ECEF;
  border-radius: 14px;
  font-size: 15px;
  transition: border-color 0.2s;
}
.email-input:focus {
  border-color: #845EC2;
  outline: none;
  box-shadow: 0 0 0 4px rgba(132, 94, 194, 0.1);
}
```

---

## 9. Landing Page Layout

### Struktur (begge varianter)
```
1. Sticky top-bar (logo + "Join Beta" knap)
2. Hero-sektion (headline + subheadline + CTA)
3. Carousel med 4 slides + dots
4. Social proof / testimonial-citat
5. Feature-highlights (3 kolonner med emoji-ikoner)
6. Email signup CTA (gentaget)
7. Footer (minimal)
```

### Responsivt grid
- **Mobil (< 640px)**: 1 kolonne, fuld bredde
- **Tablet (640-1024px)**: 2 kolonner for features
- **Desktop (> 1024px)**: 3 kolonner for features, centered max-width 1080px

---

## 10. Variant-specifikke Temaer

### Variant A: Wedding
- **Baggrund**: Bloed fersken-til-hvid gradient
- **Accent**: `#FEC5E5` (blush pink) som dekorative blobber
- **Hero-imagery**: Tidslinje-illustration med bryllups-emojis
- **Tonalitet**: Varm, tryg, "vi har styr paa det for dig"

### Variant B: Vacation
- **Baggrund**: Lys aqua-til-hvid gradient
- **Accent**: `#C9F0FF` (sky blue) + `#FFE8CC` (sand) som dekorative blobber
- **Hero-imagery**: Tidslinje-illustration med rejse-emojis
- **Tonalitet**: Afslappet, eventyrlysten, "din naeste tur, helt stressfri"

---

## 11. Tilgaengelighed

- **Kontrast**: Alle tekst/baggrund-kombinationer overholder WCAG AA (4.5:1)
- **Fokus-states**: Tydelig outline paa alle interaktive elementer
- **Reduced motion**: Respekter `prefers-reduced-motion: reduce`
- **Touch targets**: Minimum 44x44px paa alle knapper og links
- **Alt-tekst**: Beskrivende alt-tekst paa alle illustrationer
- **Semantisk HTML**: Brug korrekte landmarks, headings, og ARIA-labels

---

## 12. Performance-krav

- **Lighthouse score**: 95+ paa alle kategorier
- **First Contentful Paint**: < 1.5s
- **Total page weight**: < 200KB (inkl. fonts)
- **Ingen JavaScript-frameworks**: Vanilla JS, minimal DOM-manipulation
- **Font-loading**: `font-display: swap` for at undgaa FOIT
- **Billeder**: Inline SVG eller CSS-kun — ingen raster-billeder i MVP

---

**Dokumentversion:** 1.0
**Sidst opdateret:** 14. februar 2026
