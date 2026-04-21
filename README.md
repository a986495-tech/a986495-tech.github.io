# a986495-tech.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Malay Self-Introduction Tool</title>
    <style>
        :root {
            --primary-color: #006b3f; /* Malaysia Green */
            --accent-color: #d4af37; /* Royal Gold */
            --bg-color: #f8fafc;
            --text-color: #1e293b;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            padding: 20px;
            margin: 0;
        }
        .container {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            max-width: 600px;
            width: 100%;
        }
        h1 { color: var(--primary-color); border-bottom: 3px solid var(--accent-color); padding-bottom: 10px; }
        .form-group { margin-bottom: 20px; }
        label { display: block; font-weight: bold; margin-bottom: 5px; }
        input, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            font-size: 16px;
        }
        .result-section {
            margin-top: 30px;
            padding: 20px;
            background: #f1f5f9;
            border-left: 5px solid var(--primary-color);
            border-radius: 8px;
        }
        .sentence-block { margin-bottom: 15px; }
        .malay-text { font-size: 20px; font-weight: bold; color: var(--primary-color); display: block; }
        .ipa-text { font-size: 16px; color: #64748b; font-family: 'Lucida Sans Unicode', 'Arial Unicode MS'; }
        .translation { font-size: 16px; font-style: italic; color: #475569; }
    </style>
</head>
<body>

<div class="container">
    <h1>Malay Self-Introduction</h1>
    <p>Fill in the blanks to generate your personalized introduction with IPA phonetics.</p>
    
    <div class="form-group">
        <label for="name">Your Name</label>
        <input type="text" id="name" placeholder="e.g. John Doe" oninput="update()">
    </div>

    <div class="form-group">
        <label for="origin">Where are you from?</label>
        <input type="text" id="origin" value="Taiwan" oninput="update()">
    </div>

    <div class="form-group">
        <label for="major">What is your major?</label>
        <input type="text" id="major" value="Education" oninput="update()">
    </div>

    <div class="form-group">
        <label for="hobby">Select a Hobby</label>
        <select id="hobby" onchange="update()">
            <option value="Melancong|məlantʃoŋ|Traveling">Melancong (Traveling)</option>
            <option value="Membaca|məmbaatʃa|Reading">Membaca (Reading)</option>
            <option value="Berjoging|bəɾdʒoɡiŋ|Jogging">Berjoging (Jogging)</option>
            <option value="Mendengar muzik|məndəŋaɾ muzik|Listening to music">Mendengar muzik (Listening to music)</option>
            <option value="Mengambil gambar|məŋambil ɡambaɾ|Taking photos">Mengambil gambar (Taking photos)</option>
        </select>
    </div>

    <div class="result-section" id="result">
        </div>
</div>

<script>
    function update() {
        const name = document.getElementById('name').value || "[Name]";
        const origin = document.getElementById('origin').value || "[Origin]";
        const major = document.getElementById('major').value || "[Major]";
        const hobbyData = document.getElementById('hobby').value.split('|');
        
        const hobbyMalay = hobbyData[0];
        const hobbyIPA = hobbyData[1];
        const hobbyEng = hobbyData[2];

        const html = `
            <div class="sentence-block">
                <span class="malay-text">Apa khabar, nama saya ${name}.</span>
                <span class="ipa-text">/apa xabaɾ, nama saja ${name}/</span><br>
                <span class="translation">Hello, my name is ${name}.</span>
            </div>
            <div class="sentence-block">
                <span class="malay-text">Saya berasal dari ${origin}.</span>
                <span class="ipa-text">/saja bərasal daɾi ${origin}/</span><br>
                <span class="translation">I am from ${origin}.</span>
            </div>
            <div class="sentence-block">
                <span class="malay-text">Saya mengambil jurusan ${major}.</span>
                <span class="ipa-text">/saja məŋambil dʒuɾusan ${major}/</span><br>
                <span class="translation">My major is ${major}.</span>
            </div>
            <div class="sentence-block">
                <span class="malay-text">Hobi saya ialah ${hobbyMalay}.</span>
                <span class="ipa-text">/hobi saja jalah ${hobbyIPA}/</span><br>
                <span class="translation">My hobby is ${hobbyEng}.</span>
            </div>
        `;
        document.getElementById('result').innerHTML = html;
    }
    update(); // Initial call
</script>

</body>
</html>
