[index.html.html](https://github.com/user-attachments/files/29393301/index.html.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Order — Pauline's Pastries</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css">
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; background: #f5f4f0; color: #1a1a18; min-height: 100vh; }
.wrap { max-width: 520px; margin: 0 auto; padding: 1rem; }

.header { text-align: center; padding: 2rem 1rem 1.5rem; }
.header h1 { font-size: 24px; font-weight: 600; color: #1a1a18; }
.header p { font-size: 14px; color: #6b6b66; margin-top: 4px; }

.card { background: #fff; border-radius: 14px; border: 0.5px solid #e0dfd8; padding: 1.25rem; margin-bottom: 1rem; }
.section-title { font-size: 12px; font-weight: 600; color: #888780; text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 0.85rem; }

.min-note { font-size: 13px; color: #7a5c0a; background: #fef3d0; border: 0.5px solid #f0d070; border-radius: 8px; padding: 9px 12px; margin-bottom: 1rem; display: flex; align-items: center; gap: 8px; }

.product-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
.product-card { background: #f9f8f4; border: 0.5px solid #e0dfd8; border-radius: 12px; padding: 1rem; cursor: pointer; transition: all 0.15s; user-select: none; }
.product-card:hover { border-color: #aaa; }
.product-card.selected { border: 1.5px solid #3b82f6; background: #eff6ff; }
.product-card .name { font-size: 14px; font-weight: 600; color: #1a1a18; margin-bottom: 2px; }
.product-card .desc { font-size: 12px; color: #888780; margin-bottom: 6px; line-height: 1.4; }
.product-card .price { font-size: 13px; color: #3b82f6; font-weight: 500; }

.qty-row { display: flex; align-items: center; gap: 12px; background: #f9f8f4; border: 0.5px solid #e0dfd8; border-radius: 8px; padding: 0.7rem 1rem; margin-bottom: 8px; }
.qty-row label { font-size: 14px; color: #1a1a18; flex: 1; }
.qty-controls { display: flex; align-items: center; gap: 10px; }
.qty-btn { width: 30px; height: 30px; border: 0.5px solid #ccc; border-radius: 8px; background: #fff; color: #1a1a18; font-size: 18px; cursor: pointer; display: flex; align-items: center; justify-content: center; line-height: 1; }
.qty-btn:hover { background: #f0eeea; }
.qty-num { font-size: 15px; font-weight: 600; min-width: 22px; text-align: center; }

.counter-bar { display: flex; justify-content: space-between; align-items: center; font-size: 13px; padding: 8px 0 2px; }
.counter-bar .label { color: #888780; }
.counter-bar .count { font-weight: 600; color: #e08030; }
.counter-bar .count.ok { color: #16a34a; }

.field { margin-bottom: 0.8rem; }
.field label { font-size: 13px; color: #6b6b66; display: block; margin-bottom: 4px; }
.field input, .field textarea, .field select {
  width: 100%; font-size: 14px; padding: 9px 12px;
  border: 0.5px solid #d0cfc8; border-radius: 8px;
  background: #fff; color: #1a1a18; outline: none;
  font-family: inherit;
}
.field input:focus, .field textarea:focus, .field select:focus { border-color: #3b82f6; box-shadow: 0 0 0 2px #dbeafe; }
.field textarea { height: 72px; resize: none; }
.field select { cursor: pointer; }

.summary-rows { margin-bottom: 8px; }
.summary-row { display: flex; justify-content: space-between; font-size: 14px; color: #6b6b66; margin-bottom: 5px; }
.summary-row.total { font-weight: 600; font-size: 15px; color: #1a1a18; border-top: 0.5px solid #e0dfd8; padding-top: 8px; margin-top: 4px; }

.payment-note { font-size: 13px; color: #1e4080; background: #eff6ff; border: 0.5px solid #bfdbfe; border-radius: 8px; padding: 10px 12px; margin-bottom: 1rem; display: flex; gap: 8px; align-items: flex-start; }

.submit-btn { width: 100%; padding: 13px; font-size: 15px; font-weight: 600; background: #1a1a18; color: #fff; border: none; border-radius: 10px; cursor: pointer; transition: opacity 0.15s; }
.submit-btn:hover { opacity: 0.85; }
.submit-btn:disabled { opacity: 0.35; cursor: not-allowed; }

.success-screen { display: none; text-align: center; padding: 3rem 1.5rem; }
.success-icon { width: 56px; height: 56px; background: #dcfce7; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 1rem; font-size: 26px; }
.success-screen h2 { font-size: 20px; font-weight: 600; color: #1a1a18; margin-bottom: 8px; }
.success-screen p { font-size: 14px; color: #6b6b66; line-height: 1.7; }

/* ADMIN */
.admin-trigger { text-align: center; padding: 2rem 0 1rem; }
.admin-trigger a { font-size: 12px; color: #ccc; text-decoration: none; }
.admin-trigger a:hover { color: #888; }

.admin-panel { display: none; background: #fff; border-radius: 14px; border: 1.5px solid #3b82f6; padding: 1.25rem; margin-bottom: 1rem; }
.admin-panel h3 { font-size: 15px; font-weight: 600; color: #1a1a18; margin-bottom: 0.25rem; }
.admin-panel .sub { font-size: 12px; color: #888; margin-bottom: 1rem; }
.admin-login { display: flex; gap: 8px; margin-bottom: 1rem; }
.admin-login input { flex: 1; font-size: 14px; padding: 8px 12px; border: 0.5px solid #d0cfc8; border-radius: 8px; background: #f9f8f4; color: #1a1a18; outline: none; font-family: inherit; }
.admin-login button { padding: 8px 16px; font-size: 13px; font-weight: 600; background: #1a1a18; color: #fff; border: none; border-radius: 8px; cursor: pointer; }
.date-list { margin-bottom: 0.75rem; }
.date-item { display: flex; align-items: center; justify-content: space-between; padding: 7px 10px; background: #f9f8f4; border-radius: 8px; margin-bottom: 6px; font-size: 14px; color: #1a1a18; }
.date-item .remove { background: none; border: none; color: #e24b4a; cursor: pointer; font-size: 18px; line-height: 1; padding: 0 2px; }
.add-date-row { display: flex; gap: 8px; }
.add-date-row input { flex: 1; font-size: 14px; padding: 8px 12px; border: 0.5px solid #d0cfc8; border-radius: 8px; background: #fff; color: #1a1a18; outline: none; font-family: inherit; }
.add-date-row button { padding: 8px 14px; font-size: 13px; font-weight: 600; background: #3b82f6; color: #fff; border: none; border-radius: 8px; cursor: pointer; }
.admin-saved { font-size: 12px; color: #16a34a; margin-top: 6px; display: none; }
.no-dates { font-size: 13px; color: #aaa; font-style: italic; margin-bottom: 8px; }
</style>
</head>
<body>
<div class="wrap">

  <!-- ADMIN PANEL -->
  <div class="admin-panel" id="admin-panel">
    <h3>Admin — pickup dates</h3>
    <div class="sub">Set which dates customers can choose from.</div>
    <div id="admin-login-section">
      <div class="admin-login">
        <input type="password" id="admin-pw" placeholder="Password" onkeydown="if(event.key==='Enter')adminLogin()">
        <button onclick="adminLogin()">Unlock</button>
      </div>
      <div id="login-error" style="font-size:12px;color:#e24b4a;display:none;">Wrong password.</div>
    </div>
    <div id="admin-content" style="display:none;">
      <div class="date-list" id="date-list"></div>
      <div class="add-date-row">
        <input type="date" id="new-date-input">
        <button onclick="addDate()">Add date</button>
      </div>
      <div class="admin-saved" id="admin-saved">Saved!</div>
    </div>
  </div>

  <!-- ORDER FORM -->
  <div id="order-form">
    <div class="header">
      <h1>Pauline's Pastries</h1>
      <p>Homemade French pastries — pickup in Fremont, CA</p>
    </div>

    <div class="min-note">
      <i class="ti ti-info-circle" style="font-size:15px;flex-shrink:0;"></i>
      Minimum order: 4 pieces total (mix and match)
    </div>

    <div class="card">
      <div class="section-title">Choose items</div>
      <div class="product-grid">
        <div class="product-card" data-name="Canelé" data-price="4.00" onclick="toggleProduct(this)">
          <div class="name">Canelé</div>
          <div class="desc">Classic Bordeaux-style, caramelized crust</div>
          <div class="price">$4.00 each</div>
        </div>
        <div class="product-card" data-name="Dacquoise" data-price="7.00" onclick="toggleProduct(this)">
          <div class="name">Dacquoise</div>
          <div class="desc">Sea salt caramel coco</div>
          <div class="price">$7.00 each</div>
        </div>
      </div>

      <div id="qty-section" style="display:none; margin-top:1rem;">
        <div id="qty-list"></div>
        <div class="counter-bar">
          <span class="label">Total pieces</span>
          <span class="count" id="total-count">0 / 4 minimum</span>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="section-title">Pickup date</div>
      <div class="field">
        <div id="no-dates-msg" style="font-size:13px;color:#aaa;font-style:italic;display:none;">No pickup dates available yet. Check back soon!</div>
        <select id="pickup-date" style="display:none;">
          <option value="">Select a date...</option>
        </select>
      </div>
    </div>

    <div class="card">
      <div class="section-title">Your info</div>
      <div class="field">
        <label>Name</label>
        <input type="text" id="cust-name" placeholder="Your name">
      </div>
      <div class="field">
        <label>Phone or Instagram</label>
        <input type="text" id="cust-contact" placeholder="(510) 000-0000 or @handle">
      </div>
      <div class="field">
        <label>Notes (optional)</label>
        <textarea id="cust-notes" placeholder="Allergies, special requests, gift message..."></textarea>
      </div>
    </div>

    <div class="card" id="summary-card" style="display:none;">
      <div class="section-title">Order summary</div>
      <div class="summary-rows" id="summary-items"></div>
      <div class="summary-row total">
        <span>Total</span>
        <span id="summary-total">$0.00</span>
      </div>
    </div>

    <div class="payment-note">
      <i class="ti ti-credit-card" style="font-size:16px;flex-shrink:0;margin-top:1px;"></i>
      <span>Payment via <strong>Zelle or Venmo</strong> after your order is confirmed. I'll reach out with details.</span>
    </div>

    <button class="submit-btn" id="submit-btn" onclick="submitOrder()" disabled>Send order request</button>
  </div>

  <!-- SUCCESS -->
  <div class="success-screen" id="success-screen">
    <div class="success-icon">✓</div>
    <h2 id="success-title">Thanks!</h2>
    <p id="success-body"></p>
  </div>

  <!-- ADMIN TRIGGER -->
  <div class="admin-trigger">
    <a href="#" onclick="toggleAdmin(event)">manage pickup dates</a>
  </div>

</div>

<script>
const ADMIN_PASSWORD = 'pastry2024';
const STORAGE_KEY = 'pauline_pickup_dates';

const quantities = {};
const prices = {};
const MIN_QTY = 4;
let adminUnlocked = false;

function loadDates() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    return saved ? JSON.parse(saved) : [];
  } catch(e) { return []; }
}

function saveDates(dates) {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(dates));
}

function formatDate(d) {
  const parts = d.split('-');
  const date = new Date(parseInt(parts[0]), parseInt(parts[1])-1, parseInt(parts[2]));
  return date.toLocaleDateString('en-US', { weekday:'long', month:'long', day:'numeric' });
}

function renderPickupSelect() {
  const dates = loadDates().filter(d => d >= new Date().toISOString().split('T')[0]);
  const sel = document.getElementById('pickup-date');
  const noMsg = document.getElementById('no-dates-msg');
  sel.innerHTML = '<option value="">Select a date...</option>';
  if (dates.length === 0) {
    sel.style.display = 'none';
    noMsg.style.display = 'block';
  } else {
    noMsg.style.display = 'none';
    sel.style.display = 'block';
    dates.sort().forEach(d => {
      const opt = document.createElement('option');
      opt.value = d;
      opt.textContent = formatDate(d);
      sel.appendChild(opt);
    });
  }
}

function renderAdminDates() {
  const dates = loadDates();
  const list = document.getElementById('date-list');
  if (dates.length === 0) {
    list.innerHTML = '<div class="no-dates">No dates added yet.</div>';
    return;
  }
  list.innerHTML = dates.sort().map(d => `
    <div class="date-item">
      <span>${formatDate(d)}</span>
      <button class="remove" onclick="removeDate('${d}')">×</button>
    </div>
  `).join('');
}

function addDate() {
  const input = document.getElementById('new-date-input');
  const val = input.value;
  if (!val) return;
  const dates = loadDates();
  if (!dates.includes(val)) {
    dates.push(val);
    saveDates(dates);
    renderAdminDates();
    renderPickupSelect();
    showSaved();
  }
  input.value = '';
}

function removeDate(d) {
  const dates = loadDates().filter(x => x !== d);
  saveDates(dates);
  renderAdminDates();
  renderPickupSelect();
  showSaved();
}

function showSaved() {
  const el = document.getElementById('admin-saved');
  el.style.display = 'block';
  setTimeout(() => el.style.display = 'none', 2000);
}

function toggleAdmin(e) {
  e.preventDefault();
  const panel = document.getElementById('admin-panel');
  panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
  if (panel.style.display === 'block' && adminUnlocked) renderAdminDates();
}

function adminLogin() {
  const pw = document.getElementById('admin-pw').value;
  if (pw === ADMIN_PASSWORD) {
    adminUnlocked = true;
    document.getElementById('admin-login-section').style.display = 'none';
    document.getElementById('admin-content').style.display = 'block';
    renderAdminDates();
  } else {
    document.getElementById('login-error').style.display = 'block';
  }
}

function toggleProduct(card) {
  const name = card.dataset.name;
  const price = parseFloat(card.dataset.price);
  card.classList.toggle('selected');
  if (card.classList.contains('selected')) {
    quantities[name] = quantities[name] || 1;
    prices[name] = price;
  } else {
    delete quantities[name];
    delete prices[name];
  }
  renderQty();
  renderSummary();
  updateCounter();
}

function renderQty() {
  const selected = Object.keys(quantities);
  const section = document.getElementById('qty-section');
  const list = document.getElementById('qty-list');
  if (selected.length === 0) { section.style.display = 'none'; return; }
  section.style.display = 'block';
  list.innerHTML = selected.map(name => `
    <div class="qty-row">
      <label>${name}</label>
      <div class="qty-controls">
        <button class="qty-btn" onclick="changeQty('${name}', -1)">−</button>
        <span class="qty-num" id="qty-${name.replace(/[^a-z0-9]/gi,'_')}">${quantities[name]}</span>
        <button class="qty-btn" onclick="changeQty('${name}', 1)">+</button>
      </div>
    </div>
  `).join('');
}

function changeQty(name, delta) {
  quantities[name] = Math.max(1, (quantities[name] || 1) + delta);
  const el = document.getElementById('qty-' + name.replace(/[^a-z0-9]/gi,'_'));
  if (el) el.textContent = quantities[name];
  renderSummary();
  updateCounter();
}

function totalPieces() {
  return Object.values(quantities).reduce((s, q) => s + q, 0);
}

function updateCounter() {
  const total = totalPieces();
  const section = document.getElementById('qty-section');
  if (Object.keys(quantities).length === 0) { updateSubmitBtn(); return; }
  const countEl = document.getElementById('total-count');
  if (total >= MIN_QTY) {
    countEl.textContent = total + ' pieces ✓';
    countEl.className = 'count ok';
  } else {
    countEl.textContent = total + ' / 4 minimum';
    countEl.className = 'count';
  }
  updateSubmitBtn();
}

function updateSubmitBtn() {
  const btn = document.getElementById('submit-btn');
  btn.disabled = totalPieces() < MIN_QTY;
}

function renderSummary() {
  const names = Object.keys(quantities);
  const card = document.getElementById('summary-card');
  if (names.length === 0) { card.style.display = 'none'; return; }
  card.style.display = 'block';
  let total = 0;
  const rows = names.map(name => {
    const sub = quantities[name] * prices[name];
    total += sub;
    return `<div class="summary-row"><span>${quantities[name]}× ${name}</span><span>$${sub.toFixed(2)}</span></div>`;
  });
  document.getElementById('summary-items').innerHTML = rows.join('');
  document.getElementById('summary-total').textContent = '$' + total.toFixed(2);
}

function submitOrder() {
  const name = document.getElementById('cust-name').value.trim();
  const contact = document.getElementById('cust-contact').value.trim();
  const dateVal = document.getElementById('pickup-date').value;
  const notes = document.getElementById('cust-notes').value.trim();
  if (!name || !contact) { alert('Please fill in your name and contact info.'); return; }
  if (totalPieces() < MIN_QTY) { alert('Minimum order is 4 pieces.'); return; }
  let orderLines = Object.keys(quantities).map(n => `${quantities[n]}× ${n}`).join(', ');
  let total = Object.keys(quantities).reduce((s,n) => s + quantities[n]*prices[n], 0);
  const dateStr = dateVal ? formatDate(dateVal) : '';
  document.getElementById('order-form').style.display = 'none';
  document.getElementById('success-screen').style.display = 'block';
  document.getElementById('success-title').textContent = 'Thanks, ' + name + '!';
  document.getElementById('success-body').innerHTML =
    'Your order for <strong>' + orderLines + '</strong> (total <strong>$' + total.toFixed(2) + '</strong>) has been received' +
    (dateStr ? ' for pickup on <strong>' + dateStr + '</strong>' : '') + '.' +
    '<br><br>I\'ll reach out to you at <strong>' + contact + '</strong> to confirm and share payment details via Zelle or Venmo.' +
    (notes ? '<br><br>Notes: ' + notes : '');
}

renderPickupSelect();
</script>
</body>
</html>
