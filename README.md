<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Sharing Website</title>
    <style>
        /* CSS styles for the file-sharing website */
        body {
            background-color: #ffffff; /* Set background color to white */
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        .file-form {
            margin-bottom: 20px;
        }
        .file-list {
            list-style-type: none;
            padding: 0;
        }
        .file-item {
            background-color: #f9f9f9;
            border: 1px solid #dddddd;
            padding: 10px;
            margin-bottom: 10px;
        }
        .file-item a {
            text-decoration: none;
            color: #333333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>File Sharing Website</h1>
        
        <!-- File upload form -->
        <form class="file-form" id="file-form" enctype="multipart/form-data">
            <input type="file" name="file" id="file" multiple>
            <button type="submit">Upload File</button>
        </form>

        <!-- Uploaded files section -->
        <ul class="file-list" id="file-list">
            <!-- Files will be dynamically added here -->
        </ul>
    </div>

    <script>
        // JavaScript code to handle file upload and display
        document.getElementById('file-form').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission

            var formData = new FormData(this);
            var fileList = document.getElementById('file');

            for (var i = 0; i < fileList.files.length; i++) {
                formData.append('files[]', fileList.files[i]);
            }

            // You can now send formData to your server using AJAX or fetch API
            // Example: fetch('upload.php', { method: 'POST', body: formData })
            // .then(response => response.json())
            // .then(data => console.log(data))
            // .catch(error => console.error('Error:', error));
            
            // For demonstration purposes, we'll just display the file names
            displayFiles(fileList.files);
        });

        function displayFiles(files) {
            var fileListContainer = document.getElementById('file-list');
            fileListContainer.innerHTML = '';

            for (var i = 0; i < files.length; i++) {
                var fileItem = document.createElement('li');
                fileItem.classList.add('file-item');
                fileItem.innerHTML = '<a href="#">' + files[i].name + '</a>';
                fileListContainer.appendChild(fileItem);
            }
        }
    </script>
</body>
</html>
