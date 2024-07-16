from moviepy.editor import *
from PIL import Image, ImageDraw, ImageFont

# Example text input
text = "Hello, world! This is a sample text for generating a video."

# Step 1: Generate images from text
def text_to_image(text):
    img = Image.new('RGB', (640, 480), color = (73, 109, 137))
    d = ImageDraw.Draw(img)
    font = ImageFont.truetype("arial.ttf", 28)
    d.text((10,10), text, font=font, fill=(255, 255, 0))
    return img

# Step 2: Create video from images
def images_to_video(images):
    clips = [ImageClip(image).set_duration(2) for image in images]
    video = concatenate_videoclips(clips, method="compose")
    video.write_videofile("generated_video.mp4", fps=24)

# Example usage
if __name__ == '__main__':
    # Step 1: Generate images from text
    images = [text_to_image(text)]

    # Step 2: Create video from images
    images_to_video(images)

