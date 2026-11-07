# Magel-Inventory-Coffee-Shop


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Brew &amp; Bean — Inventory Sign In</title>
<style>
  :root {
    --brown: #6f4e37;
    --brown-dark: #4a3226;
    --cream: #f7f1e8;
    --ink: #2b211b;
    --muted: #7a6a5f;
    --line: #e2d6c8;
    --error: #b3261e;
    --ok: #2e7d32;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    min-height: 100vh;
    display: grid;
    place-items: center;
    padding: 24px;
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
    color: var(--ink);
    background: radial-gradient(circle at 20% 10%, #fff8ee, var(--cream) 60%);
  }
  .card {
    width: 100%;
    max-width: 420px;
    background: #fff;
    border: 1px solid var(--line);
    border-radius: 18px;
    padding: 32px 28px;
    box-shadow: 0 18px 40px -24px rgba(74, 50, 38, .45);
  }
  .brand {
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 700;
    letter-spacing: .02em;
    color: var(--brown-dark);
    margin-bottom: 22px;
  }
  .brand span.dot {
    width: 30px; height: 30px;
    display: grid; place-items: center;
    border-radius: 50%;
    background: var(--brown);
    color: #fff;
    font-size: 15px;
  }
  h1 { font-size: 1.35rem; margin: 0 0 6px; }
  .sub { color: var(--muted); font-size: .9rem; margin: 0 0 22px; line-height: 1.5; }
  label { display: block; font-size: .82rem; font-weight: 600; margin: 14px 0 6px; }
  input[type="text"], input[type="email"], input[type="password"], select {
    width: 100%;
    padding: 11px 13px;
    font: inherit;
    font-size: .92rem;
    color: var(--ink);
    background: #fffdfa;
    border: 1px solid var(--line);
    border-radius: 10px;
    outline: none;
    transition: border-color .15s, box-shadow .15s;
  }
  input:focus, select:focus {
    border-color: var(--brown);
    box-shadow: 0 0 0 3px rgba(111, 78, 55, .14);
  }
  .row { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-top: 16px; }
  .check { display: flex; align-items: center; gap: 8px; font-size: .84rem; color: var(--muted); font-weight: 500; margin: 0; }
  .check input { accent-color: var(--brown); }
  a { color: var(--brown); font-size: .84rem; text-decoration: none; }
  a:hover { text-decoration: underline; }
  button {
    width: 100%;
    margin-top: 22px;
    padding: 12px;
    font: inherit;
    font-weight: 600;
    color: #fff;
    background: var(--brown);
    border: 0;
    border-radius: 10px;
    cursor: pointer;
    transition: background .15s;
  }
  button:hover { background: var(--brown-dark); }
  button:disabled { opacity: .6; cursor: progress; }
  .switch { text-align: center; font-size: .86rem; color: var(--muted); margin-top: 20px; }
  .msg {
    display: none;
    margin-top: 16px;
    padding: 10px 12px;
    border-radius: 10px;
    font-size: .85rem;
    line-height: 1.45;
  }
  .msg.show { display: block; }
  .msg.error { background: #fdecea; color: var(--error); }
  .msg.ok { background: #eaf5ea; color: var(--ok); }
  .hint { font-size: .76rem; color: var(--muted); margin-top: 6px; }
  .hidden { display: none; }
  .fine { font-size: .76rem; color: var(--muted); margin-top: 18px; line-height: 1.5; }
</style>
</head>
<body>
<main class="card">
  <div class="brand"><span class="dot">☕</span> Magel &amp;  Inventory</div>

  <section id="view-login">
    <h1>Welcome back</h1>
    <p class="sub">Sign in to check stock, log deliveries and record daily counts.</p>

    <form id="login-form" novalidate>
      <label for="login-email">Email address</label>
      <input id="login-email" type="email" autocomplete="username" placeholder="name@magel.cafe" required />

      <label for="login-password">Password</label>
      <input id="login-password" type="password" autocomplete="current-password" placeholder="Your password" required />

      <div class="row">
        <label class="check"><input id="remember" type="checkbox" /> Remember me</label>
        <a href="#" id="forgot-link">Forgot password?</a>
      </div>

      <button type="submit">Sign in</button>
      <div class="msg" id="login-msg" role="alert"></div>
    </form>

    <p class="switch">New here? <a href="#" id="to-register">Create a staff account</a></p>
  </section>

  <section id="view-register" class="hidden">
    <h1>Create your staff account</h1>
    <p class="sub">New accounts are reviewed by the manager before inventory access is switched on.</p>

    <form id="register-form" novalidate>
      <label for="reg-name">Full name</label>
      <input id="reg-name" type="text" autocomplete="name" placeholder="As it appears on your staff record" required />

      <label for="reg-email">Work email</label>
      <input id="reg-email" type="email" autocomplete="email" placeholder="name@magel.cafe" required />

      <label for="reg-role">Role</label>
      <select id="reg-role" required>
        <option value="">Select your role</option>
        <option>Barista</option>
        <option>Shift lead</option>
        <option>Kitchen</option>
        <option>Manager</option>
        <<option>Owner</option>
      </select>

      <label for="reg-password">Password</label>
      <input id="reg-password" type="password" autocomplete="new-password" placeholder="At least 8 characters" required />
      <div class="hint">8+ characters, with a capital letter and a number.</div>

      <label for="reg-confirm">Confirm password</label>
      <input id="reg-confirm" type="password" autocomplete="new-password" placeholder="Type it once more" required />

      <button type="submit">Create account</button>
      <div class="msg" id="register-msg" role="alert"></div>
    </form>

    <p class="switch">Already have an account? <a href="#" id="to-login">Sign in</a></p>
  </section>

  <section id="view-reset" class="hidden">
    <h1>Reset password</h1>
    <p class="sub">Enter your work email and we'll send a reset link.</p>

    <form id="reset-form" novalidate>
      <label for="reset-email">Work email</label>
      <input id="reset-email" type="email" autocomplete="email" placeholder="name@magel.cafe" required />
      <button type="submit">Send reset link</button>
      <div class="msg" id="reset-msg" role="alert"></div>
    </form>

    <p class="switch"><a href="#" id="back-to-login">Back to sign in</a></p>
  </section>
  
</main>

<script>
(() => {
  "use strict";

  const USERS_KEY = "magel.users";
  const SESSION_KEY = "magel.session";

  const $ = (id) => document.getElementById(id);
  const views = {
    login: $("view-login"),
    register: $("view-register"),
    reset: $("view-reset"),
  };

  function show(name) {
    Object.entries(views).forEach(([key, el]) => el.classList.toggle("hidden", key !== name));
  }

  function message(el, text, type = "error") {
    el.textContent = text;
    el.className = "msg show " + type;
  }
  function clearMessage(el) {
    el.textContent = "";
    el.className = "msg";
  }

  function loadUsers() {
    try { return JSON.parse(localStorage.getItem(USERS_KEY)) || {}; }
    catch { return {}; }
  }
  function saveUsers(users) {
    localStorage.setItem(USERS_KEY, JSON.stringify(users));
  }

  async function hash(password) {
    const data = new TextEncoder().encode(password);
    const digest = await crypto.subtle.digest("SHA-256", data);
    return [...new Uint8Array(digest)].map(b => b.toString(16).padStart(2, "0")).join("");
  }

  const isEmail = (v) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v);
  const isStrong = (v) => v.length >= 8 && /[A-Z]/.test(v) && /\d/.test(v);

  $("login-form").addEventListener("submit", async (e) => {
    e.preventDefault();
    const msg = $("login-msg");
    clearMessage(msg);

    const email = $("login-email").value.trim().toLowerCase();
    const password = $("login-password").value;

    if (!isEmail(email)) return message(msg, "Enter a valid email address.");
    if (!password) return message(msg, "Enter your password.");

    const users = loadUsers();
    const user = users[email];

    if (!user) return message(msg, "No account found for that email. Create an account first.");
    if (user.status === "pending") return message(msg, "Your account is waiting for manager approval.");

    const hashed = await hash(password);
    if (hashed !== user.password) return message(msg, "That password doesn't match. Try again.");

    const session = { email, name: user.name, role: user.role, at: Date.now() };
    if ($("remember").checked) {
      localStorage.setItem(SESSION_KEY, JSON.stringify(session));
    } else {
      sessionStorage.setItem(SESSION_KEY, JSON.stringify(session));
    }

    message(msg, `Signed in as ${user.name} (${user.role}). Opening the inventory dashboard…`, "ok");
    $("login-form").reset();
  });

  $("register-form").addEventListener("submit", async (e) => {
    e.preventDefault();
    const msg = $("register-msg");
    clearMessage(msg);

    const name = $("reg-name").value.trim();
    const email = $("reg-email").value.trim().toLowerCase();
    const role = $("reg-role").value;
    const password = $("reg-password").value;
    const confirm = $("reg-confirm").value;

    if (name.length < 2) return message(msg, "Enter your full name.");
    if (!isEmail(email)) return message(msg, "Enter a valid work email address.");
    if (!role) return message(msg, "Choose your role.");
    if (!isStrong(password)) return message(msg, "Password needs 8+ characters, a capital letter and a number.");
    if (password !== confirm) return message(msg, "The passwords don't match.");

    const users = loadUsers();
    if (users[email]) return message(msg, "An account already exists for that email. Try signing in.");

    users[email] = {
      name,
      role,
      password: await hash(password),
      status: role === "Manager" ? "active" : "pending",
      created: new Date().toISOString(),
    };
    saveUsers(users);

    message(
      msg,
      role === "Manager"
        ? "Account created. You can sign in now."
        : "Account created. The manager needs to approve it before you can sign in.",
      "ok"
    );
    $("register-form").reset();
  });

  /* ---------- Reset ---------- */
  $("reset-form").addEventListener("submit", (e) => {
    e.preventDefault();
    const msg = $("reset-msg");
    clearMessage(msg);

    const email = $("reset-email").value.trim().toLowerCase();
    if (!isEmail(email)) return message(msg, "Enter a valid email address.");

    message(msg, "If that email is registered, a reset link is on its way. Check your inbox.", "ok");
    $("reset-form").reset();
  });

  $("to-register").addEventListener("click", (e) => { e.preventDefault(); show("register"); });
  $("to-login").addEventListener("click", (e) => { e.preventDefault(); show("login"); });
  $("forgot-link").addEventListener("click", (e) => { e.preventDefault(); show("reset"); });
  $("back-to-login").addEventListener("click", (e) => { e.preventDefault(); show("login"); });
})();
</script>
</body>
</html>