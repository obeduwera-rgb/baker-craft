# BakeCraft — Project Documentation
### Group Assignment IV-a · INSY 8313 — Management Information System (MIS)
### Adventist University of Central Africa · Instructor: Eric Maniraguha

---

## 1. Group Information

| Field | Details |
|---|---|
| Group members | **[Uwera Ishimwe Obed]**, **[Greg]**|
| Registration numbers | **[20251NET006]**, **[20251IMA000]** |
| Selected application/system | **BakeCraft** — a customizable bakery mobile application |
| Project Link | **[https://www.figma.com/design/hNRhNkf5GDnPzd9haz650Z/Untitled?node-id=0-1&t=Cjuzym8YdG0LLAZz-1]**
---

## 2. Problem Statement

**What problem does the application solve?**

Ordering a custom cake or pastry for an event today usually happens over WhatsApp voice notes, phone calls, or a Pinterest screenshot handed to a bakery. This creates a communication gap: customers struggle to describe exactly what they want, bakeries struggle to quote an accurate price before the design is finalized, and both sides often only discover a mismatch — wrong size, wrong flavor, wrong colors — on the day of the event, when it's too late to fix. Bakery staff also lose hours per week manually re-confirming details that could have been captured up front.

BakeCraft solves this by turning cake customization into a **visual, step-by-step builder**: customers choose size, flavor, frosting, and toppings themselves, see a live rendered preview and live price as they go, and submit an order that is already unambiguous — no back-and-forth required.

**Who are the target users?**

- Individuals planning personal events (birthdays, baby showers, anniversaries) who want a specific look without visiting the bakery in person.
- Corporate event coordinators who order recurring, branded pastries for meetings and company events.
- Small bakery staff (indirect users) who receive clearer, structured orders instead of free-text requests.

**Why is the system important?**

It reduces miscommunication and order errors, gives customers price transparency before they commit, saves bakery staff time on clarifying calls, and helps small bakeries scale personalized orders without hiring more front-of-house staff.

---

## 3. User Personas

### Persona 1 — Primary

| Field | Details |
|---|---|
| Name | Aline Uwase |
| Age | 29 |
| Occupation | Marketing Executive, Kigali |
| Goals | Order a fully customized birthday cake for her daughter that matches a specific party theme, without taking time off work to visit a bakery in person. |
| Challenges / frustrations | Screenshots she sends bakeries rarely translate into what she actually receives; she doesn't know the final price until the bakery calls back; she has very little free time during the workday to go back and forth on details. |

### Persona 2 — Secondary

| Field | Details |
|---|---|
| Name | Eric Mugisha |
| Age | 35 |
| Occupation | Corporate Events Coordinator |
| Goals | Reorder the same branded cake/pastry design (company colors and logo) for repeating company events, and get an itemized receipt for expense reporting. |
| Challenges / frustrations | Re-explaining the same custom design every time he orders; no easy way to save or duplicate a past design; needs a clear cost breakdown for finance approval. |

---

## 4. User Flow Explanation

See `assets/user-flow.svg` for the full diagram. The primary path is:

```
Splash → Onboarding → Log In / Register → Home
   → Custom Cake Builder
        1. Size & Shape → 2. Flavor & Filling → 3. Frosting & Color → 4. Toppings, Message & Candles
   → Design Preview (live render + price) → Add to Cart
   → Checkout (delivery date, time, address) → Payment
   → Order Confirmation → Order Tracking
```

**Profile / Order History** is treated as an *anytime-access hub* reachable from the bottom navigation at every stage (dashed lines in the diagram) rather than a step in the linear flow — this is what lets Eric (Persona 2) reorder a saved design directly, skipping the Builder entirely.

The flow was deliberately kept linear and forward-only through the Builder (rather than a free-form menu of options) because the core problem being solved is ambiguity — a guided sequence prevents customers from submitting an incomplete design.

---

## 5. Design Explanation

**Design system**

| Token | Value | Use |
|---|---|---|
| Ivory (background) | `#FFF6EC` | Base background, buttercream tone rather than a generic gray/cream |
| Plum (primary) | `#7A2E3E` | Primary buttons, key headers, active states |
| Caramel (secondary) | `#C98A3D` | Progress indicators, accents, utility text |
| Rose (tertiary) | `#F0B8C4` / `#E191A3` | Category chips, secondary highlights |
| Sage (confirmation) | `#7C9473` | Success states, order-confirmed screens |
| Cocoa (text) | `#3B2A26` | Body text (dark chocolate, not pure black) |

**Typography:** Fraunces (display headings — a warm, slightly soft serif that reads "handmade" rather than corporate), Nunito Sans (UI body text), Space Mono (prices and step labels — referencing the stamped price tags used in real bakeries).

**Signature element:** the app's core value proposition is *watching your cake come together in layers*, so the tiered-cake illustration is not just a logo — it is reused functionally as:
1. The Builder's step-progress indicator (each tier represents a customization step and fills in as it's completed).
2. The live design preview inside the Builder.
3. The Order Tracking status bar (Confirmed → Baking → Decorating → Out for Delivery → Delivered), reusing the same visual language post-purchase.

This ties the visual identity directly to the product's function rather than being decorative.

**Responsive/consistency notes:** all screens share the same 375×812 mobile frame, spacing scale, and component set (buttons, chips, cards) so the design is consistent across the full flow. A dark-mode variant of the Home screen is included to demonstrate the palette adapts without losing brand identity (bonus deliverable).

---

## 6. Features Implemented

- Account creation / login (email + Google)
- Category browsing (Birthday, Wedding, Corporate, Baby Shower)
- Step-by-step Custom Cake Builder (size, flavor, frosting, toppings & message) with live price calculation
- Live design preview before purchase
- Cart, delivery scheduling, and checkout
- Order confirmation and real-time order status tracking
- Profile with saved designs and one-tap reordering
- Dark mode (bonus)

---

## 7. Accessibility Considerations

- **Color contrast:** Body text (`#3B2A26` cocoa) on ivory backgrounds exceeds WCAG AA contrast requirements; primary buttons use white text on plum (`#7A2E3E`), also AA/AAA-compliant.
- **Not relying on color alone:** Builder steps and order status are labeled with text (e.g. "Baking") in addition to color, so colorblind users aren't dependent on hue alone to understand progress.
- **Readable type scale:** body copy set at 13.5px minimum with 1.5 line-height; no text below 11px, and small text is reserved for non-essential captions only.
- **Tap targets:** primary buttons and bottom-nav items are sized at a minimum 44×44px touch target.
- **Focus states:** interactive elements (buttons, inputs) include a visible focus outline in caramel for keyboard/switch-device navigation.
- **Clear, consistent navigation:** the same bottom nav (Home, Explore, Build, Orders, Profile) persists across all core screens so users always know where they are.

---

## 8. Challenges Faced

*(Edit this section based on your group's actual experience while building the Figma file.)*

- Translating a real-time "live preview" concept (normally powered by app logic) into static high-fidelity frames while still communicating that the preview updates dynamically.
- Keeping visual consistency across 10 screens while reusing a custom illustration (the tiered cake) at different scales and color states.
- Balancing a rich customization flow (4 builder steps) against the assignment's requirement for simple, uncluttered navigation.

---

## 9. Conclusion

BakeCraft demonstrates how a guided, visual builder can remove the ambiguity that typically comes with custom orders — replacing back-and-forth messaging with a structured flow that gives customers clarity and bakeries cleaner orders. The design system ties the product's core mechanic (layered customization) directly into its visual identity, reused consistently from onboarding through order tracking.

---

## 10. How This Was Built (for your group's reference)

The wireframes and high-fidelity screens were built as standalone HTML/CSS files (`wireframes/wireframes.html` and `high-fidelity-designs/high-fidelity.html`), designed to be imported into Figma using an HTML-to-Figma plugin (e.g. **html.to.design**):

1. Open Figma → open a new file → run the **html.to.design** plugin (Community plugin, free tier available).
2. Choose "Import from file" (or "Import from URL" if hosting the file), and select `high-fidelity-designs/high-fidelity.html` first, then repeat for `wireframes/wireframes.html`.
3. The plugin will convert each phone frame into a native Figma frame with editable layers, text, and fills — group members can then rename layers, adjust auto layout, and connect frames using Figma's native **Prototype** tab.
4. Build the clickable prototype by wiring: Splash → Onboarding → Login → Home → Builder (steps 1→2→3→4) → Preview → Cart → Checkout → Confirmation → Tracking, plus a persistent link from the bottom nav to Profile.
5. Set link sharing to **"Anyone with the link can view"** before submitting.

This keeps the group's actual hands-on Figma work (required by the assignment) focused on interaction and prototyping, while the structural and visual design work is already done.
