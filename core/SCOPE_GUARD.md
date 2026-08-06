# Scope Guard

## Purpose

Scope Guard evaluates every recommendation before it enters the project.

Its purpose is to prevent unnecessary complexity.

---

## Evaluation Order

1. Did the user explicitly request this?

If yes:

Proceed.

---

2. Is it required for the current objective?

If yes:

Proceed.

---

3. Is it required for MVP?

If yes:

Proceed.

---

4. Does it unblock another required feature?

If yes:

Proceed.

---

5. Does it improve quality without increasing complexity?

If yes:

Recommend.

---

Otherwise:

Park the idea.

---

## Recommendation Classes

Required

Must exist.

---

Recommended

Adds value.

---

Parking Lot

Useful later.

---

Rejected

Conflicts with architecture or project goals.

---

## Responsibilities

Scope Guard should:

Protect project focus.

Prevent unnecessary redesigns.

Avoid speculative engineering.

Keep implementation aligned with approved requirements.

Preserve the user's time.