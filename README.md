<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Download Multiple PDFs from GitHub</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }

        .download-button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            margin: 5px;
        }

        .download-button:hover {
            background-color: #45a049;
        }

        .image-container {
            margin-bottom: 20px;
        }

        .image-container img {
            max-width: 300px; 
            width: 100%;     
            height: auto;    
            border: 2px solid #4CAF50;
        }
    </style>
</head>
<body>
    
    <div id="buttons-container">
        <!-- Buttons and images will be generated here -->
    </div>

    <script>
        const pdfFiles = [
            { name: 'Drawing 5 Drawing v3', url: 'https://raw.githubusercontent.com/googlefind/hi/a3cc15f25d35bbd0c0ea3204d958b0c3d5454b4b/Drawing%205%20Drawing%20v3.pdf', imgUrl: 'https://raw.githubusercontent.com/googlefind/hi/addb682a1e3af49bee42a6ebba24cc5527a6d877/Screenshot%202025-01-01%20193539.png' },
            { name: 'Plummer block', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Plummer%20Block%20Drawing%20v7.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193553.png' },
            { name: 'Socket and spigot cotter', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Socket%20and%20spigot%20cotter%20Drawing%20v3.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193602.png' },
            { name: 'Ramsbottom safety valve', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Ramsbottom%20Safety%20valve%20%20%202%20Drawing%20%202...%20v2.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193611.png' },
            { name: 'ISO tread form', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/ISO%20Thread%20Form%20Drawing%20v1.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193618.png' },
            { name: 'Drawing 1', url: 'https ://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Drawing%20Drawing%201.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193625.png' },
            { name: 'Drawing 0', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Drawing%200.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193633.png' },
            { name: 'Machine vice drawing v5', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Machine%20Vice%20Drawing%20v5.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193641.png' },
            { name: 'Drawing 2 Drawing', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Drawing%202%20Drawing%20v3.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193649.png' },
            { name: 'Connecting Rod drawing', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/Connecting%20Rod%20Drawing%20v4.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193657.png' },
            { name: 'New File 1', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%201.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193710.png' },
            { name: 'New File 2', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%202.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193720.png' },
            { name: 'New File 3', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%203.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193727.png' },
            { name: 'New File 4', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%204.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193734.png' },
            { name: 'New File 5', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%205.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193741.png' },
            { name: 'New File 6', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%206.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193754.png' },
            { name: 'New File 7', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%207.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193801.png' },
            { name: 'New File 8', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%208.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193808.png' },
            { name: 'New File 9', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%209.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193819.png' },
            { name: 'New File 10', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%2010.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193835.png' },
            { name: 'New File 11', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/New%20File%2011.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193842.png' },
            { name: 'New File 12', url: 'https://raw.githubusercontent.com/googlefind/hi/blob/b51521341195036e3c25601efd8e973834a73511/4%20Drawing%20v3.pdf', imgUrl: 'https://github.com/googlefind/hi/raw/edc4a78269a1cab678ce36d39babcf7aede7343b/Screenshot%202025-01-01%20193848.png' },
        ];

        const buttonsContainer = document.getElementById('buttons-container');

        pdfFiles.forEach(file => {
            const container = document.createElement('div');
            container.className = 'image-container';

            const img = document.createElement('img');
            img.src = file.imgUrl;
            img.alt = file.name;

            const button = document.createElement('a');
            button.href = file.url;
            button.className = 'download-button';
            button.innerText = `Download ${file.name}`;
            button.download = ''; // This attribute allows direct download

            container.appendChild(img);
            container.appendChild(button);
            buttonsContainer.appendChild(container);
        });
    </script>
    <p>MR_VD</p>
</body>
</html>
