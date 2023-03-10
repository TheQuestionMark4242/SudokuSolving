template <class T> struct segTree{
    //Segment tree for range that supports any associative operation like sum, prod, max, min
    //Use as: segTree<int> s;
    int n;
    vector<T> seg;
    T cmb(T a, T b){return a + b;} //Combiner function, use max instead for max segtree
    const T ID{0};//Identity for combiner, i.e. cmb(ID, a) = a for all a, INT_MIN for max for example
    
    segTree(int _n) : n(_n){ seg.assign(2*n, ID); }
    void pull(int p){ seg[p] = cmb(seg[2*p], seg[2*p+1]);}
    void upd(int p, T val){ //Update value at position p to val
        seg[p += n] = val;
        for(p/=2; p; p/=2) pull(p);
    }
    T query(int l, int r){//Return combined value over range [l, r] both ends inclusive
        T ra = ID, rb = ID;
        for(l += n, r += n + 1; l < r; l/=2, r/=2){
            if(l%2) ra = cmb(ra, seg[l++]);
            if(r%2) rb = cmb(seg[--r], rb);
        }
        return cmb(ra, rb);
    }
};
