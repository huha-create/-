<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, shrink-to-fit=no">
  <title>PartsPhone — запчасти и ремонт телефонов</title>
  <!-- Font Awesome 6 для иконок -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Roboto, system-ui, -apple-system, sans-serif;
    }

    body {
      background: #f5f7fb;
      color: #1e293b;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 0 20px;
      width: 100%;
    }

    /* Шапка */
    header {
      background: white;
      box-shadow: 0 4px 20px rgba(0,0,0,0.03);
      padding: 15px 0;
      position: sticky;
      top: 0;
      z-index: 50;
    }
    .header-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 15px;
    }
    .logo {
      font-size: 1.8rem;
      font-weight: 700;
      color: #0f172a;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .logo i {
      color: #2563eb;
      font-size: 2rem;
    }
    .logo span {
      color: #2563eb;
    }
    .header-contacts {
      display: flex;
      align-items: center;
      gap: 15px;
      color: #334155;
      font-weight: 500;
    }
    .header-contacts i {
      color: #2563eb;
      margin-right: 5px;
    }
    .btn {
      background: white;
      border: 1px solid #e2e8f0;
      padding: 10px 20px;
      border-radius: 30px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: #1e293b;
      background: #f8fafc;
    }
    .btn-primary {
      background: #2563eb;
      border: 1px solid #2563eb;
      color: white;
      box-shadow: 0 4px 10px rgba(37,99,235,0.2);
    }
    .btn-primary:hover {
      background: #1d4ed8;
    }
    .btn:hover {
      background: #f1f5f9;
      border-color: #cbd5e1;
    }
    .btn-primary:hover {
      background: #1d4ed8;
      border-color: #1d4ed8;
    }

    /* Hero / табы категорий */
    .category-section {
      background: white;
      border-radius: 24px;
      padding: 20px;
      margin: 25px 0 15px;
      box-shadow: 0 10px 25px -5px rgba(0,0,0,0.05);
    }
    .category-tabs {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
    }
    .cat-tab {
      padding: 12px 28px;
      border-radius: 40px;
      font-weight: 600;
      background: #f1f5f9;
      border: none;
      cursor: pointer;
      transition: 0.2s;
      font-size: 1rem;
      display: flex;
      align-items: center;
      gap: 8px;
      color: #334155;
    }
    .cat-tab i {
      font-size: 1.2rem;
    }
    .cat-tab.active {
      background: #2563eb;
      color: white;
      box-shadow: 0 8px 18px rgba(37,99,235,0.3);
    }
    .cat-tab:hover:not(.active) {
      background: #e2e8f0;
    }

    /* Сетка объявлений */
    .listings-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 24px;
      margin: 20px 0 30px;
    }
    .card {
      background: white;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 10px 20px rgba(0,0,0,0.04);
      transition: transform 0.2s, box-shadow 0.2s;
      display: flex;
      flex-direction: column;
      border: 1px solid #f1f5f9;
    }
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 20px 30px rgba(0,0,0,0.08);
    }
    .card-img {
      height: 200px;
      background: #f8fafc;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }
    .card-img img {
      max-width: 80%;
      max-height: 80%;
      object-fit: contain;
    }
    .card-img .placeholder-icon {
      font-size: 3.5rem;
      color: #cbd5e1;
    }
    .card-body {
      padding: 18px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }
    .card-title {
      font-weight: 700;
      font-size: 1.2rem;
      margin-bottom: 6px;
    }
    .card-meta {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.85rem;
      color: #64748b;
      margin-bottom: 10px;
    }
    .badge {
      background: #dbeafe;
      color: #1e40af;
      padding: 4px 12px;
      border-radius: 20px;
      font-weight: 600;
      font-size: 0.75rem;
      display: inline-block;
    }
    .specs {
      font-size: 0.9rem;
      color: #475569;
      margin: 8px 0 12px;
      line-height: 1.5;
    }
    .price {
      font-weight: 700;
      font-size: 1.4rem;
      color: #0f172a;
      margin-top: auto;
    }
    .card-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 12px;
    }

    /* Форма добавления */
    .add-listing-panel {
      background: white;
      border-radius: 24px;
      padding: 25px;
      margin: 20px 0 35px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.05);
      border: 1px solid #e9eef2;
    }
    .form-title {
      font-size: 1.5rem;
      font-weight: 700;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 18px;
    }
    .form-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .form-group label {
      font-weight: 600;
      font-size: 0.9rem;
      color: #334155;
    }
    input, select, textarea {
      padding: 12px 16px;
      border: 1px solid #e2e8f0;
      border-radius: 14px;
      font-size: 0.95rem;
      background: #f8fafc;
      transition: 0.2s;
    }
    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: #2563eb;
      background: white;
    }
    .file-upload {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .btn-outline {
      background: white;
      border: 1px dashed #94a3b8;
      padding: 10px 18px;
      border-radius: 30px;
    }
    .preview-img {
      width: 50px;
      height: 50px;
      border-radius: 12px;
      object-fit: cover;
      background: #f1f5f9;
    }

    footer {
      margin-top: auto;
      background: white;
      padding: 18px 0;
      text-align: center;
      color: #64748b;
      border-top: 1px solid #e2e8f0;
    }

    .empty-state {
      text-align: center;
      grid-column: 1 / -1;
      padding: 40px;
      color: #64748b;
    }

    @media (max-width: 600px) {
      .header-inner {
        flex-direction: column;
        align-items: flex-start;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="container header-inner">
      <div class="logo">
        <i class="fas fa-mobile-alt"></i> Parts<span>Phone</span>
      </div>
      <div class="header-contacts">
        <span><i class="fas fa-phone-alt"></i> +7 (999) 123-45-67</span>
        <span><i class="fas fa-tools"></i> Ремонт и запчасти</span>
      </div>
      <button class="btn" id="scrollToAddBtn"><i class="fas fa-plus-circle"></i> Добавить объявление</button>
    </div>
  </header>

  <main class="container">
    <!-- Категории -->
    <div class="category-section">
      <div class="category-tabs" id="categoryTabs">
        <button class="cat-tab active" data-category="all"><i class="fas fa-th-large"></i> Все</button>
        <button class="cat-tab" data-category="iphone"><i class="fab fa-apple"></i> iPhone</button>
        <button class="cat-tab" data-category="samsung"><i class="fas fa-mobile-alt"></i> Samsung</button>
        <button class="cat-tab" data-category="android"><i class="fab fa-android"></i> Android</button>
      </div>
    </div>

    <!-- Сетка объявлений -->
    <div id="listingsContainer" class="listings-grid">
      <!-- Динамически заполняется JS -->
    </div>

    <!-- Форма добавления -->
    <div class="add-listing-panel" id="addListingPanel">
      <div class="form-title">
        <i class="fas fa-pen-to-square"></i> Новое объявление
      </div>
      <div class="form-grid">
        <div class="form-group">
          <label>Название детали</label>
          <input type="text" id="partName" placeholder="Например: Дисплей iPhone 12">
        </div>
        <div class="form-group">
          <label>Категория</label>
          <select id="partCategory">
            <option value="iphone">iPhone</option>
            <option value="samsung">Samsung</option>
            <option value="android">Android</option>
          </select>
        </div>
        <div class="form-group">
          <label>Цена (₽)</label>
          <input type="number" id="partPrice" placeholder="4500">
        </div>
        <div class="form-group">
          <label>Характеристики</label>
          <input type="text" id="partSpecs" placeholder="OLED, 6.1\", оригинал">
        </div>
        <div class="form-group">
          <label>Фото детали</label>
          <div class="file-upload">
            <input type="file" id="partImage" accept="image/*" style="display:none;">
            <button type="button" class="btn-outline" id="uploadTrigger"><i class="fas fa-camera"></i> Выбрать фото</button>
            <img id="imagePreview" class="preview-img" src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='40' height='40' viewBox='0 0 24 24' fill='%23cbd5e1'%3E%3Crect width='24' height='24' fill='%23f1f5f9'/%3E%3Cpath d='M4 5h16v14H4z' fill='%23e2e8f0'/%3E%3Ccircle cx='8.5' cy='8.5' r='1.5' fill='%23cbd5e1'/%3E%3C/svg%3E" alt="preview">
          </div>
        </div>
        <div class="form-group" style="align-self: end;">
          <button class="btn btn-primary" id="addListingBtn"><i class="fas fa-check"></i> Опубликовать</button>
        </div>
      </div>
    </div>
  </main>

  <footer>
    <div class="container">
      <p>© PartsPhone — запчасти для телефонов и профессиональный ремонт</p>
    </div>
  </footer>

  <script>
    (function() {
      // Хранилище объявлений
      let listings = [];

      // Демо-данные для старта
      const demos = [
        {
          id: 1,
          name: 'Дисплей iPhone 13 Pro',
          category: 'iphone',
          price: 12500,
          specs: 'OLED 6.1", Face ID, оригинал',
          image: null
        },
        {
          id: 2,
          name: 'Аккумулятор Samsung S22',
          category: 'samsung',
          price: 3200,
          specs: '4500 мАч, оригинал',
          image: null
        },
        {
          id: 3,
          name: 'Шлейф кнопки Home iPhone 8',
          category: 'iphone',
          price: 850,
          specs: 'Touch ID, оригинал',
          image: null
        },
        {
          id: 4,
          name: 'Стекло камеры Xiaomi 12',
          category: 'android',
          price: 700,
          specs: 'Защитное стекло объектива',
          image: null
        }
      ];

      // Загрузка из localStorage или демо
      function loadListings() {
        const stored = localStorage.getItem('phonePartsListings');
        if (stored) {
          listings = JSON.parse(stored);
        } else {
          listings = [...demos];
          saveListings();
        }
      }

      function saveListings() {
        localStorage.setItem('phonePartsListings', JSON.stringify(listings));
      }

      // Текущая категория
      let currentCategory = 'all';

      // Рендер карточек
      function renderListings() {
        const container = document.getElementById('listingsContainer');
        if (!container) return;
        
        const filtered = currentCategory === 'all' 
          ? listings 
          : listings.filter(item => item.category === currentCategory);

        if (filtered.length === 0) {
          container.innerHTML = `<div class="empty-state"><i class="fas fa-box-open" style="font-size:2rem; opacity:0.5;"></i><p>Нет объявлений в этой категории</p></div>`;
          return;
        }

        container.innerHTML = filtered.map(item => {
          const imageHtml = item.image 
            ? `<img src="${item.image}" alt="${item.name}">` 
            : `<i class="fas fa-microchip placeholder-icon"></i>`;
          
          return `
            <div class="card">
              <div class="card-img">
                ${imageHtml}
              </div>
              <div class="card-body">
                <div class="card-title">${escapeHtml(item.name)}</div>
                <div class="card-meta">
                  <span class="badge">${getCategoryLabel(item.category)}</span>
                </div>
                <div class="specs">${escapeHtml(item.specs) || 'Характеристики не указаны'}</div>
                <div class="price">${item.price.toLocaleString()} ₽</div>
                <div class="card-footer">
                  <span style="font-size:0.8rem; color:#64748b;">В наличии</span>
                  <button class="btn" onclick="deleteListing(${item.id})" title="Удалить"><i class="fas fa-trash"></i></button>
                </div>
              </div>
            </div>
          `;
        }).join('');
      }

      function escapeHtml(text) {
        return String(text).replace(/[&<>"]/g, function(m) {
          if (m === '&') return '&amp;';
          if (m === '<') return '&lt;';
          if (m === '>') return '&gt;';
          if (m === '"') return '&quot;';
          return m;
        });
      }

      function getCategoryLabel(cat) {
        const map = {
          iphone: 'iPhone',
          samsung: 'Samsung',
          android: 'Android'
        };
        return map[cat] || cat;
      }

      // Добавление объявления
      function addListing() {
        const nameInput = document.getElementById('partName');
        const categorySelect = document.getElementById('partCategory');
        const priceInput = document.getElementById('partPrice');
        const specsInput = document.getElementById('partSpecs');
        const imageInput = document.getElementById('partImage');
        
        const name = nameInput.value.trim();
        const category = categorySelect.value;
        const price = parseFloat(priceInput.value);
        const specs = specsInput.value.trim();

        if (!name) {
          alert('Введите название детали');
          return;
        }
        if (isNaN(price) || price <= 0) {
          alert('Укажите корректную цену');
          return;
        }

        const newListing = {
          id: Date.now(),
          name,
          category,
          price,
          specs,
          image: imagePreviewDataUrl || null
        };

        listings.push(newListing);
        saveListings();
        
        // Очистка формы
        nameInput.value = '';
        priceInput.value = '';
        specsInput.value = '';
        clearImagePreview();
        
        renderListings();
        
        // Прокрутка к объявлениям
        document.getElementById('listingsContainer').scrollIntoView({ behavior: 'smooth', block: 'start' });
      }

      // Удаление
      window.deleteListing = function(id) {
        if (confirm('Удалить это объявление?')) {
          listings = listings.filter(item => item.id !== id);
          saveListings();
          renderListings();
        }
      };

      // Работа с изображением (превью + base64)
      let imagePreviewDataUrl = null;
      
      function setupImageUpload() {
        const fileInput = document.getElementById('partImage');
        const trigger = document.getElementById('uploadTrigger');
        const preview = document.getElementById('imagePreview');
        
        trigger.addEventListener('click', () => fileInput.click());
        
        fileInput.addEventListener('change', function(e) {
          const file = e.target.files[0];
          if (!file) return;
          
          const reader = new FileReader();
          reader.onload = function(ev) {
            imagePreviewDataUrl = ev.target.result;
            if (preview) {
              preview.src = imagePreviewDataUrl;
            }
          };
          reader.readAsDataURL(file);
        });
      }

      function clearImagePreview() {
        imagePreviewDataUrl = null;
        const preview = document.getElementById('imagePreview');
        if (preview) {
          preview.src = "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='40' height='40' viewBox='0 0 24 24' fill='%23cbd5e1'%3E%3Crect width='24' height='24' fill='%23f1f5f9'/%3E%3Cpath d='M4 5h16v14H4z' fill='%23e2e8f0'/%3E%3Ccircle cx='8.5' cy='8.5' r='1.5' fill='%23cbd5e1'/%3E%3C/svg%3E";
        }
        const fileInput = document.getElementById('partImage');
        if (fileInput) fileInput.value = '';
      }

      // Переключение категорий
      function setupCategories() {
        const tabs = document.querySelectorAll('.cat-tab');
        tabs.forEach(tab => {
          tab.addEventListener('click', function() {
            tabs.forEach(t => t.classList.remove('active'));
            this.classList.add('active');
            currentCategory = this.dataset.category;
            renderListings();
          });
        });
      }

      // Кнопка скролла к форме
      function setupScrollButton() {
        const btn = document.getElementById('scrollToAddBtn');
        const panel = document.getElementById('addListingPanel');
        if (btn && panel) {
          btn.addEventListener('click', () => {
            panel.scrollIntoView({ behavior: 'smooth' });
          });
        }
      }

      // Инициализация
      document.addEventListener('DOMContentLoaded', function() {
        loadListings();
        renderListings();
        setupCategories();
        setupImageUpload();
        setupScrollButton();
        
        const addBtn = document.getElementById('addListingBtn');
        if (addBtn) {
          addBtn.addEventListener('click', addListing);
        }
      });
    })();
  </script>
</body>
</html>
