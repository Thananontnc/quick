# Implementation Plan: KeyCraft Picker (JS Edition)

## 1. Schema Refactoring (Gap Analysis Updates)
To align with the project scope, the `Part` schema's `specs` map must strictly enforce the following structure based on `type`:

### Case Specs 
- `layout`: String (e.g., "60%", "TKL")
- `mountingType`: String (e.g., "Tray", "Gasket")
- `supportedLayouts`: Array of Strings (e.g., ["60%", "65%"])

### PCB Specs
- `layout`: String
- `mountingType`: String
- `switchSupport`: String ("3-pin" or "5-pin")
- `hotSwap`: Boolean

### Switch Specs
- `brand`: String (e.g., "Cherry", "Gateron")
- `switchType`: String ("Linear", "Tactile", "Clicky")
- `pricePerUnit`: Number

### Keycap Specs
- `material`: String (e.g., "ABS", "PBT")
- `layoutSupport`: Array of Strings

## 2. Backend Updates
- **Validation:** Update `POST /api/parts` to reject requests missing these specific fields.
- **Populate:** Ensure `GET /api/builds` properly populates these nested spec fields.

## 3. Frontend Updates
- **Admin Form:** Update `AdminDashboard.jsx` to show specific input fields based on the selected Part Type.
- **Part Display:** Update `PartBrowser` and `Builder` to show these specific details (e.g., show "Linear" for switches).

---
## (Previous Sections Preserved Below)

### 3. Frontend Pages (React)
Located in `client/src/...`
...
