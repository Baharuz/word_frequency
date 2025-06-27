from collections import Counter

def word_frequency(text):
    text = text.lower()
    text = ''.join(char if char.isalnum() or char.isspace() else ' ' for char in text)
    words = text.split()
    return Counter(words)

def print_statistics(freq_dict):
    total_words = sum(freq_dict.values())
    sorted_items = freq_dict.most_common()

    print(f"\nToplam Kelime Sayısı: {total_words}")
    print("Kelime Frekansları (En sık olandan en aza):")
    for word, freq in sorted_items:
        print(f"'{word}': {freq} kez")

    if sorted_items:
        max_freq = sorted_items[0][1]
        most_common_words = [word for word, freq in sorted_items if freq == max_freq]
        if len(most_common_words) == 1:
            print(f"\nEn sık geçen kelime: '{most_common_words[0]}' ({max_freq} kez)")
        else:
            joined_words = "', '".join(most_common_words)
            print(f"\nEn sık geçen kelimeler: '{joined_words}' ({max_freq} kez)")

if __name__ == "__main__":
    input_text = input("Bir metin giriniz: ")
    result = word_frequency(input_text)
    print_statistics(result)
