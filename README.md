<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cherry's - Menu</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: #000;
            color: #fff;
            overflow-x: hidden;
        }

        /* Homepage Styles */
        .homepage {
            height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 800"><rect fill="%23d40000" width="1200" height="800"/><path fill="%23b80000" d="M0 400L50 383.3C100 366.7 200 333.3 300 316.7C400 300 500 300 600 333.3C700 366.7 800 433.3 900 450C1000 466.7 1100 433.3 1150 416.7L1200 400V800H1150C1100 800 1000 800 900 800C800 800 700 800 600 800C500 800 400 800 300 800C200 800 100 800 50 800H0V400Z"/></svg>');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            animation: fadeIn 1s ease-in;
        }

        .logo {
            font-size: 4rem;
            font-weight: 700;
            color: #fff;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.7);
            margin-bottom: 2rem;
            animation: slideDown 1s ease-out;
        }

        .logo span {
            color: #d40000;
        }

        .menu-btn {
            background: linear-gradient(45deg, #d40000, #ff3333);
            color: white;
            border: none;
            padding: 20px 60px;
            font-size: 1.5rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(212, 0, 0, 0.3);
            animation: pulse 2s infinite;
        }

        .menu-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(212, 0, 0, 0.5);
        }

        /* Menu Categories Page */
        .categories-page {
            display: none;
            min-height: 100vh;
            background: #000;
            padding: 2rem;
            animation: slideUp 0.5s ease-out;
        }

        .categories-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .category-card {
            background: linear-gradient(135deg, #1a1a1a, #2d2d2d);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .category-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }

        .category-card:hover::before {
            left: 100%;
        }

        .category-card:hover {
            transform: translateY(-10px);
            border-color: #d40000;
            box-shadow: 0 15px 30px rgba(212, 0, 0, 0.3);
        }

        .category-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .category-title {
            font-size: 1.5rem;
            font-weight: 600;
            color: #fff;
            margin-bottom: 0.5rem;
        }

        /* Category Items Page */
        .items-page {
            display: none;
            min-height: 100vh;
            background: #000;
            padding: 2rem;
            animation: fadeIn 0.5s ease-in;
        }

        .items-container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .page-header {
            text-align: center;
            margin-bottom: 3rem;
        }

        .page-title {
            font-size: 3rem;
            color: #d40000;
            margin-bottom: 1rem;
        }

        .back-btn {
            background: #d40000;
            color: white;
            border: none;
            padding: 10px 30px;
            font-size: 1rem;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 2rem;
        }

        .back-btn:hover {
            background: #ff3333;
            transform: translateX(-5px);
        }

        .items-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .item-card {
            background: #1a1a1a;
            border-radius: 15px;
            padding: 1.5rem;
            border: 1px solid #333;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .item-card:hover {
            border-color: #d40000;
            transform: scale(1.05);
            box-shadow: 0 10px 25px rgba(212, 0, 0, 0.2);
        }

        .item-name {
            font-size: 1.2rem;
            font-weight: 600;
            color: #fff;
            margin-bottom: 0.5rem;
        }

        .item-price {
            font-size: 1.5rem;
            color: #d40000;
            font-weight: 700;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .logo {
                font-size: 3rem;
            }
            
            .menu-btn {
                padding: 15px 40px;
                font-size: 1.2rem;
            }
            
            .categories-container {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }
            
            .page-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Homepage -->
    <div class="homepage" id="homepage">
        <h1 class="logo"><span>Cherry's</span></h1>
        <button class="menu-btn" onclick="showCategories()">Menu</button>
    </div>

    <!-- Categories Page -->
    <div class="categories-page" id="categoriesPage">
        <div class="page-header">
            <h1 class="page-title">Nos Catégories</h1>
        </div>
        <div class="categories-container">
            <div class="category-card" onclick="showItems('fastfood')">
                <div class="category-icon">🍔</div>
                <h3 class="category-title">Fast-food</h3>
            </div>
            <div class="category-card" onclick="showItems('pizzas')">
                <div class="category-icon">🍕</div>
                <h3 class="category-title">Les Pizzas</h3>
            </div>
            <div class="category-card" onclick="showItems('grillade')">
                <div class="category-icon">🥩</div>
                <h3 class="category-title">Nos Grillades</h3>
            </div>
            <div class="category-card" onclick="showItems('mixtes')">
                <div class="category-icon">🍱</div>
                <h3 class="category-title">Les mixtes à partager</h3>
            </div>
            <div class="category-card" onclick="showItems('glace')">
                <div class="category-icon">🍦</div>
                <h3 class="category-title">Glace</h3>
            </div>
            <div class="category-card" onclick="showItems('cafe')">
                <div class="category-icon">☕</div>
                <h3 class="category-title">Café</h3>
            </div>
            <div class="category-card" onclick="showItems('the')">
                <div class="category-icon">🍵</div>
                <h3 class="category-title">Thé</h3>
            </div>
            <div class="category-card" onclick="showItems('mocktail')">
                <div class="category-icon">🍹</div>
                <h3 class="category-title">Mocktail</h3>
            </div>
        </div>
    </div>

    <!-- Items Pages -->
    <div class="items-page" id="itemsPage">
        <div class="items-container">
            <button class="back-btn" onclick="showCategories()">← Retour</button>
            <div class="page-header">
                <h1 class="page-title" id="categoryTitle"></h1>
            </div>
            <div class="items-grid" id="itemsGrid"></div>
        </div>
    </div>

    <script>
        const menuData = {
            fastfood: {
                title: "Fast-food",
                items: [
                    { name: "Gyros au poulet", price: "3000f" },
                    { name: "Gyros au bœuf", price: "2000f" },
                    { name: "Gyros cherry's", price: "4500f" },
                    { name: "Sandwich viande", price: "1000f" },
                    { name: "Sandwich poulet", price: "1500f" },
                    { name: "Chawarma poulet", price: "2000f" },
                    { name: "Chawarma viande", price: "1500f" },
                    { name: "Hamburger", price: "2500f" },
                    { name: "Chiken burgers", price: "3000f" },
                    { name: "Cherry's burgers", price: "4000f" },
                    { name: "KFC", price: "4000f" },
                    { name: "Plat de Nems 4 pièces", price: "2500f" },
                    { name: "Tacos viande", price: "2500f" },
                    { name: "Tacos poulet", price: "3500f" },
                    { name: "Tacos cherry's", price: "4500f" },
                    { name: "Big Sandwich", price: "7500f" },
                    { name: "Big burgers", price: "7500f" }
                ]
            },
            pizzas: {
                title: "Les Pizzas",
                items: [
                    { name: "Pizza cherry's", price: "7000f" },
                    { name: "Pizza marguarita", price: "5000f" },
                    { name: "Pizza orientale", price: "6000f" },
                    { name: "Pizza végétarien", price: "6000f" },
                    { name: "Pizza Kiss", price: "6500f" }
                ]
            },
            grillade: {
                title: "Nos Grillades",
                items: [
                    { name: "Brochette de bœuf", price: "6000f" },
                    { name: "Brochette de poulet", price: "6000f" },
                    { name: "Brochette de capitaine", price: "7000f" },
                    { name: "1/2 poulet", price: "6000f" }
                ]
            },
            mixtes: {
                title: "Les mixtes à partager",
                items: [
                    { name: "Mixte fast-food", desc: "tacos viande, Chawarma poulet, nems, kfc, gyros cherry's", price: "15000f" },
                    { name: "Mixte grille", desc: "Brochette de bœuf, capitaine et 1/2 poulet", price: "15000f" }
                ]
            },
            glace: {
                title: "Glace",
                items: [
                    { name: "Une boule", price: "1000f" },
                    { name: "Deux boule", price: "1500f" },
                    { name: "Trois boule", price: "2000f" },
                    { name: "Cornet 2 boule", price: "2000f" },
                    { name: "Cornet 3 boule", price: "2500f" },
                    { name: "Cornet Américain 1 boule", price: "1000f" },
                    { name: "Cornet Américain 2 boule", price: "1500f" },
                    { name: "Wafeles bowls 1 boule", price: "2000f" },
                    { name: "Wafeles bowls 2 boules", price: "2500f" }
                ]
            },
            cafe: {
                title: "Café",
                items: [
                    { name: "Nespresso", price: "1500f" },
                    { name: "Cappuccino", price: "2000f" },
                    { name: "Frappucino glacé", price: "2500f" }
                ]
            },
            the: {
                title: "Thé",
                items: [
                    { name: "Thé mixte", price: "1500f" },
                    { name: "Thé Cherry's", price: "1500f" },
                    { name: "Thé malien", price: "1000f" }
                ]
            },
            mocktail: {
                title: "Mocktail",
                items: [
                    { name: "Ener cherry's", price: "2000f" },
                    { name: "Virginie colada", price: "4000f" },
                    { name: "Virginie mojito", price: "4000f" },
                    { name: "Bora bora", price: "4000f" },
                    { name: "San francisco", price: "4000f" },
                    { name: "Coco lait", price: "5000f" }
                ]
            }
        };

        function showCategories() {
            document.getElementById('homepage').style.display = 'none';
            document.getElementById('itemsPage').style.display = 'none';
            document.getElementById('categoriesPage').style.display = 'block';
        }

        function showItems(category) {
            const categoryData = menuData[category];
            document.getElementById('categoryTitle').textContent = categoryData.title;
            
            const itemsGrid = document.getElementById('itemsGrid');
            itemsGrid.innerHTML = '';
            
            categoryData.items.forEach(item => {
                const itemCard = document.createElement('div');
                itemCard.className = 'item-card';
                itemCard.innerHTML = `
                    <h3 class="item-name">${item.name}</h3>
                    ${item.desc ? `<p style="color: #ccc; font-size: 0.9rem; margin-bottom: 0.5rem;">${item.desc}</p>` : ''}
                    <p class="item-price">${item.price}</p>
                `;
                itemsGrid.appendChild(itemCard);
            });
            
            document.getElementById('categoriesPage').style.display = 'none';
            document.getElementById('itemsPage').style.display = 'block';
        }
    </script>
</body>
</html>
