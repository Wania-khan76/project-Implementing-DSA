class LRUCache:
    def __init__(self, capacity):
        self.totalSize = capacity
        self.cache = []

    def put(self, key, value):
        # Check for duplicate key
        for i in self.cache:
            if i[0] == key:
                # Index contains the index of the list element that is to be deleted
                index = self.cache.index(i)
                del self.cache[index]
                self.cache.append([key, value])
                return 0

        # Append when length is smaller than the size
        if len(self.cache) < self.totalSize:
            self.cache.append([key, value])
            return 1
        else:
            # Pop the first element and append the given one at the last
            del self.cache[0]
            self.cache.append([key, value])
            return 1

    def get(self, key):
        status = False
        for i in self.cache:
            if i[0] == key:
                temp = [i[0], i[1]]
                # Index contains the index of the list element that is to be deleted
                index = self.cache.index(i)
                del self.cache[index]
                self.cache.append(temp)
                status = True
                return temp[1]
        if not status:
            return -1


def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True


def generate_primes(start, end):
    primes = []
    for num in range(start, end + 1):
        if is_prime(num):
            primes.append(num)
    return primes


# Create an LRU cache with a size of 50
lru_cache = LRUCache(50)

# Scenario 1: Fill the cache with keys 0-49
miss_1 = 0
count_1 = 0
for i in range(50):
    count_1 += 1
    miss_1 += lru_cache.put(i, i)

# Print cache state after scenario 1
print("\n\033[1;95mCache after filling with keys 0-49:\n\033[0m")
print(lru_cache.cache)

# Scenario 2: Retrieve the odd-numbered key values
miss_2 = 0
count_2 = 0
print("\n\033[1;34mRetrieving Odd Keys:\n\033[0m")
for i in range(1, 100, 2):
    count_2 += 1
    value = lru_cache.get(i)
    if value != -1:
        print(f"Key: {i}, Value: {value}")
    else:
        miss_2 += 1

# Print cache state after scenario 2
print("\n\033[1;34mCache after retrieving odd-numbered keys:\n\033[0m")
print(lru_cache.cache)

# Scenario 3: Fill the cache with prime number keys 0-100
miss_3 = 0
count_3 = 0
primes = generate_primes(0, 100)
for prime in primes:
    count_3 += 1
    miss_3 += lru_cache.put(prime, prime)

# Print cache state after scenario 3
print("\n\033[1;92mCache after filling with prime number keys 0-100:\n\033[0m")
print(lru_cache.cache)

# Print the final cache state in a different color
print("\n\033[1;96mFinal Cache State:\n\033[0m")
print(lru_cache.cache)

# Initial Miss Rate
miss_rate_1 = (miss_1 / count_1) * 100
print(f"\n\033[96mInitial Miss Rate: {miss_rate_1:.2f}%\033[0m", "\n")

# Odd Number Miss Rate
miss_rate_2 = (miss_2 / count_2) * 100
print(f"\033[93mOdd Number Miss Rate: {miss_rate_2:.2f}%\033[0m", "\n")

# Prime Number Miss Rate
miss_rate_3 = (miss_3 / count_3) * 100
print(f"\033[95mPrime Number Miss Rate: {miss_rate_3:.2f}%\033[0m", "\n")

# Total miss rate
total_miss_rate = ((miss_1 + miss_2 + miss_3) / (count_1 + count_2 + count_3)) * 100
print(f"\033[91mTotal Miss Rate: {total_miss_rate:.2f}%\033[0m", "\n")
