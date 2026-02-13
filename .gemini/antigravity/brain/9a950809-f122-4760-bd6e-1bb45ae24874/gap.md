# Gap Analysis Report

## 1. Project Title & Scope
- **Compliance:** 100%
- **Current:** "KeyCraft Picker", Web App, Login/Admin, Builder, Compatibility.
- **Verdict:** Aligned.

## 2. Technology Stack
- **Compliance:** 100%
- **Requirement:** React (Vite), Vanilla CSS, Next.js (App Router), MongoDB.
- **Current:** React + Vite, Vanilla CSS (`index.css`), Next.js App Router, MongoDB.
- **Verdict:** Aligned.

## 3. Data Models (Critical Gaps Identify)
The user requested specific entities with distinct fields. Currently, we use a single `Part` schema with a dynamic `specs` map. We should refactor this to better match the requested structure, or ensure `specs` strictly enforces these fields.

**Entity 1: KeyboardCase**
- *Missing/Generic:* `layout`, `mountingType`, `supportedLayouts`.
- *Action:* Ensure `specs` contains exactly these keys for type 'case'.

**Entity 2: PCB**
- *Missing/Generic:* `switchSupport` (Hot-swap/Solder), `mountingType`.
- *Action:* Ensure `specs` contains exactly these keys for type 'pcb'.

**Entity 3: Switch**
- *Missing/Generic:* `brand`, `switchType` (Linear/Tactile/Clicky), `pricePerUnit`.
- *Action:* Ensure `specs` contains exactly these keys for type 'switch'.

**Entity 4: Keycap**
- *Missing/Generic:* `layoutSupport`, `material`.
- *Action:* Ensure `specs` contains exactly these keys for type 'keycap'.

**Entity 5: KeyboardBuild**
- *Compliance:* Aligned (References User and Parts, tracks Total Price).

## 4. Features
- **Delete Parts:** Admin dashboard has delete button (Mocked/Alert only). Needs real API implementation.
- **Edit Parts:** Missing.
- **Edit/Delete Builds:** Missing.
- **Compatibility Logic:** Needs to strictly use the new fields (`mountingType` match, `switchSupport`).

## Plan of Action
1.  **Refactor Schemas:** Update `PartSchema` to explicitly include these fields or add strict validation for `specs`.
    *Decision:* Keep `Part` collection for simplicity (Single Table Inheritance) but formalize the `specs` structure in code/validation.
2.  **Update Seed Data:** Ensure seed data populates these specific fields.
3.  **Update Backend Logic:**
    - Update `POST /api/parts` to validate these specific fields based on type.
    - Implement `DELETE /api/parts/:id`.
    - Implement `DELETE /api/builds/:id`.
4.  **Update Frontend:**
    - `AdminDashboard`: Add fields for Brand, Material, Mounting Type, etc.
    - `Builder`: Display these specific details.
    - `Compatibility`: Refine logic to compare `mountingType` (Case vs PCB) and `switchSupport`.
