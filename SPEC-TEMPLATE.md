# FEATURE SPECIFICATION: [Feature Name]

## 1. Core Objective
[A 2-3 sentence high-level summary of what this feature is, why it exists, and the primary user outcome. Do not include implementation details here.]

## 2. Architecture & Data Models
[Strict schema definitions to prevent the AI agent from hallucinating database columns or types.]
*   **Model/Table:** `[Table Name]`
    *   `id`: UUID (Primary Key)
    *   `created_at`: Timestamp (Auto-generated)
    *   `[Field Name]`: [Type] - [Constraint/Notes]

## 3. API Contracts / Routing
[Explicit definitions of endpoints or internal functions.]
*   **Endpoint:** `[GET/POST] /api/v1/...`
*   **Request Payload:** `{ "key": "type" }`
*   **Expected Response (200):** `{ "status": "success", "data": {...} }`

## 4. Acceptance Criteria
[A checklist of exact conditions the feature must meet to be considered complete. The AI agent will use this to self-verify.]
- [ ] UI component renders without console errors.
- [ ] Database successfully writes new records matching the schema.
- [ ] Authentication middleware properly blocks unauthorized requests.
- [ ] Test suite executes and passes for this module.

## 5. Edge Cases & Error Handling
[Pre-defined error handling requirements so the agent does not guess.]
*   **Scenario A:** If user inputs invalid data -> Return 400 Bad Request with standardized error JSON.
*   **Scenario B:** If database connection times out -> Retry 3 times, then fail gracefully and log to console.
