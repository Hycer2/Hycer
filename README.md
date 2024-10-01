document.getElementById('uploadForm').addEventListener('submit', function (e) {
    e.preventDefault();
    
    const fileInput = document.getElementById('file');
    const file = fileInput.files[0];

    if (file) {
        const reader = new FileReader();
        reader.onload = function (e) {
            const fileURL = e.target.result;
            const gallery = file.type.startsWith('image/') ? 'photo-gallery' : 'video-gallery';
            const galleryElement = document.getElementById(gallery);

            if (file.type.startsWith('image/')) {
                const img = document.createElement('img');
                img.src = fileURL;
                galleryElement.appendChild(img);
            } else if (file.type.startsWith('video/')) {
                const video = document.createElement('video');
                video.src = fileURL;
                video.controls = true;
                galleryElement.appendChild(video);
            }
        };
        reader.readAsDataURL(file);
    }
});
