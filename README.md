# Brandon Kluzek

I build tools for studying how AI systems reason, learn, and fail.

## About me

I’m an engineer with a background in engineering physics and production data systems. I like problems that begin as sketches and end as experiments you can run, inspect, and challenge.

## Projects

### ♟️ Chess Intelligence Lab

> **Question:** When a model chooses the wrong move, where did the reasoning fail?

Chess offers exact rules and replayable positions, which makes it a useful laboratory for model behavior. The lab treats a move as the end of a chain: read the board, follow the protocol, stay legal, calculate, compare candidates, and choose.

Each stage gets its own check so a plausible answer cannot hide the underlying failure. The goal is an inspectable benchmark with frozen tasks, failure labels, and replay records—then, once the measurement layer is trustworthy, experiments that test whether feedback or training improves performance on unseen positions.

$$\mathrm{pass}(x,m)=I_{\mathrm{parse}}(m)\,I_{\mathrm{protocol}}(m)\,I_{\mathrm{legal}}(x,m)\,\mathbf{1}\!\left[m\in A(x)\right]$$

Here, $x$ is the task, $m$ is the proposed move, and $A(x)$ is the exact accepted set. Every gate must succeed.

| Input | Measurement | Evidence |
| :--- | :--- | :--- |
| Position + task | Parse → protocol → legality → exact check | Failure label + replay |

<!-- Future links: repository | benchmark | results -->

---

### 🧠 Adaptive Study Lab

> **Question:** When is AI feedback reliable enough to shape what a learner sees next?

Adaptive Study Lab asks how model judgment can help a learner without silently becoming the learning system. A model compares a free-form answer with a hidden rubric and returns structured feedback, while scheduling, history, and study state stay local, deterministic, and inspectable. Keeping judgment separate from control makes questionable evaluations reviewable rather than authoritative.

The project is developing the full loop—material, recall, evaluation, stored evidence, and the next review—while measuring where the grader is consistent, where it disagrees, and when the system should refuse to act.

$$r_t=G_\theta(a_t,\rho),\qquad z_{t+1}=F(z_t,r_t)$$

The model grader $G_\theta$ compares answer $a_t$ with rubric $\rho$; the deterministic function $F$ owns the study-state transition.

| Input | Judgment | Control |
| :--- | :--- | :--- |
| Prompt + learner response | Model vs. hidden rubric | Local scheduler + history |

<!-- Future links: repository | demo | notes -->

---

### ◇ Structural Game Theory

> **Question:** What survives when the same strategic system is written in a different form?

Structural Game Theory asks which features belong to a strategic system and which come from the way we write it down. Starting with exact finite games, it studies relabelings, payoff transformations, rankings, best responses, and symmetries using computation and formal arguments. Small cases make every transformation and counterexample inspectable.

The aim is a reusable language for comparing games by structure rather than surface form—and a verifier that keeps mathematical claims, computational evidence, and future experiments on strategic agents clearly separated.

$$u'_i(a_i,a_{-i})=\alpha_i u_i(a_i,a_{-i})+\beta_i,\qquad \alpha_i>0\Longrightarrow\mathrm{BR}'_i(a_{-i})=\mathrm{BR}_i(a_{-i})$$

A positive affine payoff transformation preserves a player’s best-response set—one concrete example of a structural invariant.

| Object | Transformation | Check |
| :--- | :--- | :--- |
| Finite game | Relabel / rescale / transform | Invariant or counterexample |

<!-- Future links: paper | verifier | repository -->

---

## Say hello

Working on something around model evaluation, reasoning, post-training, or AI for science? [Email me](mailto:brandonkluzek@gmail.com).
