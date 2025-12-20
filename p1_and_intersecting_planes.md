# Formal ASCII Specification of P1 (Phi) and Intersecting Planes

This document specifies the P1 contract using **ASCII-style formal notation**.

No LaTeX rendering is assumed.

---

## 0. Primitive Sets and Notation

Let:

- S = set of all possible system states
- U = set of users
- L = set of lifecycle states
- O = set of observable summaries
- P = set of sharing policies
- T = discrete index set for system evolution (time / event order)

For any system state s in S:

- A(s) = set of P1 artifacts that exist in state s

Artifacts are part of the system state and may be created or removed over time.

---

## 1. P1 Artifact Interface (State-Dependent)

For each state s in S and each artifact a in A(s), the following interface functions exist:

- id(a)                  -> global artifact identifier
- owner(a, s)            -> element of U
- policy(a, s)           -> element of P
- lifecycle(a, s)        -> element of L
- observe(a, s)          -> element of O
- ref(a, b, s)           -> boolean (explicit reference)
- parent(a, b, s)        -> boolean (version edge)
- access(u, a, s)        -> boolean
- content(a, s)          -> uninterpreted internal payload

P1 requires only that these interfaces exist.
P1 does not prescribe schemas, storage, transport, or encoding.

---

## 2. Planes as Constraints on States

A constraint plane is a subset of system states.

Formally:

- A plane P is any subset of S
- Equivalently, a plane may be represented by a predicate C_P(s) returning true or false

Examples:
- P_Arch    = architecture and invariants plane
- P_Auth    = authentication and sharing plane
- P_Future_i = future constraint planes

---

## 3. System Evolution Model

System evolution is modeled as a trace:

- tau : T -> S

where tau(t) is the system state at step t.

Invariants may constrain:
- individual states
- or all states along valid traces

---

## 4. Definition of the P1 Plane

Define the P1 contract Phi as a predicate:

- Phi(a, s) -> true or false

The P1 plane is the set of states where all existing P1 artifacts satisfy Phi.

Formally:

- P1 = { s in S | for all a in A(s): Phi(a, s) = true }

---

## 5. Explicit Definition of the P1 Contract Phi

An artifact a in A(s) satisfies Phi(a, s) if and only if all invariants below hold.

---

### I1 — Single Ownership

Every artifact has exactly one owner in every state.

Formal:

- for all s in S:
    for all a in A(s):
        there exists exactly one u in U such that owner(a, s) = u

---

### I2 — Immutable Ownership Across Evolution

Ownership does not change across system evolution.

Formal:

- for all traces tau:
    for all times t1, t2 in T:
        for all a in A(tau(t1)) intersect A(tau(t2)):
            owner(a, tau(t1)) = owner(a, tau(t2))

---

### I3 — Access Determined Solely by Explicit Policy

Access is fully determined by the artifact’s explicit sharing policy.

Formal:

- for all s in S:
    for all u in U:
        for all a in A(s):
            access(u, a, s) = f(policy(a, s), u, s)

where f is an unspecified function.
P1 does not define access semantics, only that access derives from explicit policy.

---

### I4 — Stable, Globally Unique Identity

Uniqueness:

- for all s in S:
    for all a, b in A(s):
        if a != b then id(a) != id(b)

Stability across evolution:

- for all traces tau:
    for all times t1, t2 in T:
        for all a in A(tau(t1)) intersect A(tau(t2)):
            id(a) is identical in tau(t1) and tau(t2)

---

### I5 — Explicit, Acyclic Version History

Define the version graph in state s:

- vertices: A(s)
- directed edges: (b -> a) if parent(a, b, s) = true

Acyclicity:

- for all s in S:
    there does not exist an artifact a in A(s)
    such that a is reachable from itself via one or more version edges

---

### I6 — Explicit Dependencies Only

All inter-artifact dependencies are represented by explicit references.

Formal rule:

- ref(a, b, s) is the only sanctioned mechanism for artifact-level dependency

No other plane may introduce hidden or implicit coupling between artifacts.

(This invariant constrains how other planes may interact with P1 artifacts.)

---

### I7 — Referential Integrity

Every reference must target an existing artifact and be authorized by policy.

Formal:

- for all s in S:
    for all a, b in A(s):
        if ref(a, b, s) = true then:
            b exists in A(s)
            and AllowedRef(a, b, s) = true

AllowedRef is derived solely from explicit sharing policies.
Its semantics are defined outside P1.

---

### I8 — Content Opacity

P1 validity does not depend on artifact internal payloads.

Define P1-equivalence between states s and s':

- s and s' are P1-equivalent if all of the following are equal:
    id
    owner
    policy
    lifecycle
    observe
    ref
    parent

Formal:

- if s and s' are P1-equivalent then:
    for all a in A(s):
        Phi(a, s) = Phi(a, s')

Therefore, changing content alone cannot affect P1 validity.

---

### I9 — Uniform Lifecycle Model

All artifacts share the same lifecycle state set.

Formal:

- for all s in S:
    for all a in A(s):
        lifecycle(a, s) is an element of L

P1 does not define lifecycle semantics, only uniformity.

---

### I10 — Uniform Observability Surface

All artifacts expose observations in a common codomain.

Formal:

- for all s in S:
    for all a in A(s):
        observe(a, s) is an element of O

Analytics and indexing must operate through this surface.

---

### I11 — Closure Under Composition (Operation Preservation)

Let compose be any sanctioned operation that creates new artifacts.

Formal:

- if s is in P1
  and s' = compose(s, a1, a2, ..., an)
  then s' is also in P1

Composition must preserve all P1 invariants.

---

### I12 — Future-Plane Neutrality

Phi depends only on the P1 interface defined in this document.

Formal restriction:

- Phi may reference only:
    id, owner, policy, lifecycle, observe, ref, parent

Phi may not reference:
- storage details
- UI concerns
- analytics semantics
- authorization mechanics
- future constraint logic

---

## 6. Complete Definition of Phi

Phi(a, s) is true if and only if:

- I1 and I2 and I3 and I4 and I5 and I6 and I7 and I8 and I9 and I10 and I11 and I12 all hold

---

## 7. Feasible Operating Region

Let P2, P3, ..., Pn be other constraint planes.

The system may operate only in states that satisfy all planes:

- Omega = intersection of P1, P2, ..., Pn

---

## 8. Gelling Condition (Formal)

Define the P1 projection of a state s:

- pi_P1(s) =
    ids
    owners
    policies
    lifecycles
    observations
    reference graph
    version graph

A plane Pi gels with P1 if:

- there exists a predicate psi_i such that
- for all s in S:
    C_Pi(s) = psi_i(pi_P1(s))

Meaning:

- Pi may constrain P1 artifacts only via P1-observable structure
- Pi may not inspect content or branch on artifact type

---

## 9. Formal Payoff

Adding a new artifact kind extends A(s).

If new artifacts satisfy Phi, then:

- P1 remains valid
- existing planes remain unchanged
- growth restricts valid states instead of reshaping structure

---

## 10. One-Line Formal Summary

- P1 = { s in S | for all a in A(s): Phi(a, s) = true }
- Omega = intersection of all planes
- All planes interact with P1 only through pi_P1

This specification is intended to remain invariant under all future system evolution.
