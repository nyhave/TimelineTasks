# TimelineTasks A/B Landing Page Plan

## Overview

We are testing **two different landing page variants** to validate early interest in TimelineTasks.  
The goal is to measure **email signup conversion** before building a backend.

- **Target audience:** Adults 20–45, primarily women, planning personal mini-projects
- **Primary metric:** Email submissions
- **Secondary metric:** Engagement (time on page, carousel interactions)

---

## Variant A: Wedding-Focused Landing Page

**Purpose:** Test a high-emotion, high-urgency personal project as the entry wedge.

### Hero Section
- **Headline:** Plan Your Wedding Without the Chaos
- **Subheadline:** Turn your big day into a clear, beautiful timeline — so you always know what’s next and nothing gets forgotten.
- **CTA:** Join Early Beta

### Carousel
- **Slide 1:** Overview of wedding timeline at a glance  
  *Caption:* See your entire wedding timeline at a glance
- **Slide 2:** Milestones (venue, guests, dress, budget)  
  *Caption:* Break it into milestones
- **Slide 3:** Task detail and deadlines  
  *Caption:* Track tasks and progress clearly
- **Slide 4:** Progress overview  
  *Caption:* Feel calm knowing you’re on track

### Design / Visual Style
- Soft, neutral warm background  
- Elegant typography  
- Minimal, calm UI cards  
- Subtle feminine aesthetic, but not stereotypical pink  

### Key Notes
- Emotional urgency: Very high  
- Focused, concrete scenario  
- Goal: Maximize early signups for high-intent users

---

## Variant B: Vacation-Focused Landing Page

**Purpose:** Test a more general mini-project scenario with broader appeal.

### Hero Section
- **Headline:** Plan Your Next Vacation Without Stress
- **Subheadline:** Map your trips step-by-step with a visual timeline so nothing gets forgotten.
- **CTA:** Join Early Beta

### Carousel
- **Slide 1:** Trip overview  
  *Caption:* See your entire vacation plan at a glance
- **Slide 2:** Milestones (flights, hotel, packing, activities)  
  *Caption:* Break it into milestones
- **Slide 3:** Task detail and deadlines  
  *Caption:* Track tasks and progress clearly
- **Slide 4:** Progress overview  
  *Caption:* Feel calm knowing you’re on track

### Design / Visual Style
- Soft pastel tones  
- Lifestyle imagery or neutral templates  
- Minimal, clean cards  
- Gender-neutral but visually appealing to women  

### Key Notes
- Emotional urgency: Medium  
- Broader audience, but less immediate urgency  
- Goal: Test appeal to users outside wedding planning

---

## Carousel Requirements (Both Variants)
- Auto-rotating every 4 seconds  
- Smooth fade animation  
- Clickable dots indicator  
- Mobile swipe support  
- Fully static → suitable for GitHub Pages

---

## Email Signup Form
- Embedded Google Form or Typeform  
- Fields: Email, one optional qualifying question (“What project are you planning?”)  
- Clear note: Early prototype, no guarantees  
- Primary CTA under hero and carousel

---

## A/B Testing Plan
1. Deploy Variant A and Variant B on **two separate GitHub Pages URLs**  
2. Drive traffic via social media, email lists, or small ad spend (optional)  
3. Track:  
   - Email form submissions  
   - Carousel interactions (optional)  
   - Time on page  
4. Compare conversion rates after ~2–4 weeks  
5. Winner determines which direction to build first

---

## Notes for Builder
- All elements must be **static HTML/CSS/JS**, no backend required  
- Carousel must be lightweight, responsive, and touch-enabled  
- Signup form is external, static embed  
- Keep visuals aspirational, relatable, and simple  
- Focus copy on **emotional outcome**, not features

---

**End of A/B Landing Page Specification**