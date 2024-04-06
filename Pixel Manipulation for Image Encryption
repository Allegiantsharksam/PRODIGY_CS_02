from PIL import Image
import numpy as np

class ImageEncryptor:
    def __init__(self, key):
        self.key = key

    def encrypt(self, image_path, encrypted_image_path):
        img = Image.open(image_path)
        img_array = np.array(img)
        encrypted_img_array = (img_array + self.key) % 256
        encrypted_img = Image.fromarray(np.uint8(encrypted_img_array))
        encrypted_img.save(encrypted_image_path)

    def decrypt(self, encrypted_image_path, decrypted_image_path):
        encrypted_img = Image.open(encrypted_image_path)
        encrypted_img_array = np.array(encrypted_img)
        decrypted_img_array = (encrypted_img_array - self.key) % 256
        decrypted_img = Image.fromarray(np.uint8(decrypted_img_array))
        decrypted_img.save(decrypted_image_path)

def main():
    key = int(input("Enter the encryption key (an integer between 0 and 255): "))
    encryptor = ImageEncryptor(key)

    image_path = input("Enter the path of the image to encrypt: ")
    encrypted_image_path = input("Enter the path to save the encrypted image: ")
    encryptor.encrypt(image_path, encrypted_image_path)
    print(f"Encrypted image is saved as {encrypted_image_path}")

    decrypted_image_path = input("Enter the path to save the decrypted image: ")
    encryptor.decrypt(encrypted_image_path, decrypted_image_path)
    print(f"Decrypted image is saved as {decrypted_image_path}")

if __name__ == "__main__":
    main()
