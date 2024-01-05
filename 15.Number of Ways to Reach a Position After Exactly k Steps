#pragma GCC optimize("O3")
class Solution {
public:
    const int mod=1e9 + 7; // This is a prime number
    // Find x such that ax= 1 (mod b) b=mod
    int modInverse(int a, int b) {//Extended Euclidean Algorthm
        int x0 = 1, x1 = 0;
        int r0 = a, r1 = b;
        while (r1 != 0) {
            int q = r0/r1, rr = r1, xx = x1;
            r1 = r0-q * r1;
            x1 = x0-q * x1;
            r0 = rr;
            x0 = xx;
        }
        if (x0 < 0) x0+= b;// Take positive
        return x0;
    }

    int numberOfWays(int s, int e, int k) {
        int diff = s - e;
        if (k < abs(diff) || (k - diff) & 1) return 0;
        if (k==abs(diff)) return 1;
        int c = (diff >= 0) ? (k - diff) >> 1 : (k + diff) >> 1;
        vector<int> inverse(c+1, 0);
        inverse[1] = 1;
        #pragma unroll
        for (int i = 2; i <= c; i++) {
            inverse[i] = modInverse(i, mod);
        }
        long long ans = 1LL;
        #pragma unroll
        for (int i = 1; i <= c; i++) {
            ans = (ans*(k - i + 1) % mod) * inverse[i] % mod;
        }
        return ans;
    }
};
