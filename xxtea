def mx(z, y, sum, e, k, p):
    return (((z >> 5) ^ (y << 2)) + (((y >> 3) ^ (z << 4)) ^ (sum ^ y)) + (k[(((p) & (3)) ^ e)] ^ z)) & 0xffffffff

def xxtea_encrypt(v, n, k):
    DELTA = 0x9e3779b9
    z = v[n - 1]
    y = v[0]
    sum = 0

    if n > 1:
        q = 6 + 52 // n
        while (q > 0):
            sum += DELTA
            e = (sum >> 2) & 3
            p = 0
            while (p < n-1):
                 y = v[p + 1]
                 v[p] += mx(z, y, sum, e, k, p)
                 v[p] &= 0xffffffff
                 z = v[p]
                 p += 1

            y = v[0]
            v[n - 1] += mx(z, y, sum, e, k, p)
            v[n - 1] &= 0xffffffff
            z = v[n - 1]
            q -= 1

    return v
