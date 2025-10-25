# GAB
This website is made to upload my photograph photo 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Art Gallery Museum</title>
    <style>
        body {
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #2c3e50, #34495e);
            color: #ecf0f1;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow-x: hidden;
        }
        .gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            max-width: 1200px;
            padding: 20px;
        }
        .frame {
            position: relative;
            width: 300px;
            height: 400px;
            background: #f5f5dc;
            border: 10px solid #8b4513;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            transition: transform 0.3s ease;
        }
        .frame:hover {
            transform: scale(1.05);
        }
        .frame img {
            max-width: 100%;
            max-height: 100%;
            object-fit: cover;
        }
        .upload-section {
            margin-bottom: 40px;
            text-align: center;
        }
        .upload-btn {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            font-family: 'Georgia', serif;
            cursor: pointer;
            border-radius: 5px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            transition: background 0.3s ease;
        }
        .upload-btn:hover {
            background: #c0392b;
        }
        input[type="file"] {
            display: none;
        }
        h1 {
            font-size: 3em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        .placeholder {
            font-style: italic;
            color: #bdc3c7;
        }
    </style>
</head>
<body>
    <h1>Art Gallery Museum</h1>
    <div class="upload-section">
        <label for="photo-upload" class="upload-btn">Upload Your Artwork</label>
        <input type="file" id="photo-upload" accept="image/*">
    </div>
    <div class="gallery" id="gallery">
        <div class="frame">
            <div class="placeholder">Your Art Here</div>
        </div>
        <!-- Add more placeholder frames if desired -->
    </div>

    <script>
        const uploadInput = document.getElementById('photo-upload');
        const gallery = document.getElementById('gallery');

        uploadInput.addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    // Create a new frame for the uploaded image
                    const newFrame = document.createElement('div');
                    newFrame.className = 'frame';
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    newFrame.appendChild(img);
                    gallery.appendChild(newFrame);
                };
                reader.readAsDataURL(file);
            }
        });
    </script>
</body>
</html>
