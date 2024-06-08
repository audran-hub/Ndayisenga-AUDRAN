# Ndayisenga-AUDRAN
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <div class="gallery-container">
        <div class="thumbnails">
            <!-- Thumbnails will be dynamically added here -->
        </div>
        <div class="full-size-image">
            <!-- Full-size image will be displayed here -->
        </div>
    </div>
    <script src="js/script.js"></script>
</body>
</html>
#css
body {
    font-family: Arial, sans-serif;
}

.gallery-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.thumbnails {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
}

.thumbnail {
    width: 100px;
    height: 100px;
    cursor: pointer;
}

.full-size-image img {
    max-width: 100%;
    max-height: 80vh;
    display: none;
}

@media (min-width: 768px) {
    .gallery-container {
        flex-direction: row;
    }

    .thumbnails {
        flex-direction: column;
    }
}
#javascript
document.addEventListener('DOMContentLoaded', () => {
    const images = [
        'image1.jpg', 'image2.jpg', 'image3.jpg', // Add paths to your images
    ];
    const thumbnailsContainer = document.querySelector('.thumbnails');
    const fullSizeImageContainer = document.querySelector('.full-size-image');

    // Load thumbnails
    images.forEach((image, index) => {
        const thumbnail = document.createElement('img');
        thumbnail.src = `path/to/thumbnails/${image}`;
        thumbnail.classList.add('thumbnail');
        thumbnail.addEventListener('click', () => displayFullSizeImage(index));
        thumbnailsContainer.appendChild(thumbnail);
    });

    // Display full-size image
    function displayFullSizeImage(index) {
        fullSizeImageContainer.innerHTML = '';
        const fullSizeImage = document.createElement('img');
        fullSizeImage.src = `path/to/fullsize/${images[index]}`;
        fullSizeImageContainer.appendChild(fullSizeImage);
        fullSizeImage.style.display = 'block';
    }
});
# python
def has_contiguous_subarray_with_sum(arr, target):
    current_sum = 0
    start = 0

    for end in range(len(arr)):
        current_sum += arr[end]
        
        # Shrink the window as long as current_sum is greater than the target
        while current_sum > target and start <= end:
            current_sum -= arr[start]
            start += 1
        
        # Check if current_sum equals the target
        if current_sum == target:
            return True

    return False

# Example usage:
arr = [4, 2, 7, 1, 9, 5]
target = 17
print(has_contiguous_subarray_with_sum(arr, target))  # Output: True

# python 2
def transform_string(s):
    length = len(s)
    
    if length % 15 == 0:
        # If length is divisible by 15, reverse the string and then replace each character with its ASCII code
        s = s[::-1]
        s = ' '.join(str(ord(char)) for char in s)
    elif length % 5 == 0:
        # If length is divisible by 5, replace each character with its ASCII code
        s = ' '.join(str(ord(char)) for char in s)
    elif length % 3 == 0:
        # If length is divisible by 3, reverse the string
        s = s[::-1]
    
    return s

# Test cases
print(transform_string("Hamburger"))  # Output: "regrubmaH"
print(transform_string("Pizza"))      # Output: "80 105 122 122 97"
print(transform_string("Chocolate Chip Cookie"))  # Output: "eikooCpihCetalocohC"
