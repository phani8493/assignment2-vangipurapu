# assignment2-vangipurapu
webapps assignment2
# NAGA VEERA PHANEENDRA VANGIPURAPU
###### Leicester
There are so many indian restaurents like KAYAL, BOMBAY IN, **CHAIWALA**, and so many buffet providing restarurents like **FEAST INDIA**.

---

# AIRPORT TO LEICESTER
BIRMINGHAM
1. BIRMINGHAM AIRPORT TO BUS STATION 
2. GET A BUS TO ST.MARGERETTS BUS STATION.
3. GET ARRIVA LOCAL BUS TO GO TO LEICESTER CITY CENTRE 

FOOD ITEMS I RECOMMEND FROM LEICESTER
* SAMOSA
* MASALA DOSA

link to [ABOUTME.MD](https://github.com/phani8493/assignment2-vangipurapu/blob/main/ABOUTME.MD)

---

# TABLES

The following table explains the sports details

| sport/activity | Location | Equipment Fee|
| --- | --- | ---: |
| Kabaddi | Maryville | 100 |
| Cricket | Kansas | 200 |
| Soccer | St Lous | 150 |
| Shooting | NewYork | 200 |

---

# Pithy Quotes

> “Resolutely train yourself to attain peace.” By *Goutham Buddha*

> “Get busy living or get busy dying.” — *Stephen King*

---

# Code Fencing

> Graham's Scan Algorithm is an efficient algorithm for finding the convex hull of a finite set of points in the plane with time complexity O(N log N). The algorithm finds all vertices of the convex hull ordered along its boundary. It uses a stack to detect and remove concavities in the boundary efficiently.

It is named after Ronald Graham, who published the original algorithm in 1972.

> Convex Hull construction link to <https://iq.opengenus.org/graham-scan-convex-hull/>

```

struct pt {
    double x, y;
};

int orientation(pt a, pt b, pt c) {
    double v = a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y);
    if (v < 0) return -1; // clockwise
    if (v > 0) return +1; // counter-clockwise
    return 0;
}

bool cw(pt a, pt b, pt c, bool include_collinear) {
    int o = orientation(a, b, c);
    return o < 0 || (include_collinear && o == 0);
}
bool collinear(pt a, pt b, pt c) { return orientation(a, b, c) == 0; }

void convex_hull(vector<pt>& a, bool include_collinear = false) {
    pt p0 = *min_element(a.begin(), a.end(), [](pt a, pt b) {
        return make_pair(a.y, a.x) < make_pair(b.y, b.x);
    });
    sort(a.begin(), a.end(), [&p0](const pt& a, const pt& b) {
        int o = orientation(p0, a, b);
        if (o == 0)
            return (p0.x-a.x)*(p0.x-a.x) + (p0.y-a.y)*(p0.y-a.y)
                < (p0.x-b.x)*(p0.x-b.x) + (p0.y-b.y)*(p0.y-b.y);
        return o < 0;
    });
    if (include_collinear) {
        int i = (int)a.size()-1;
        while (i >= 0 && collinear(p0, a[i], a.back())) i--;
        reverse(a.begin()+i+1, a.end());
    }

    vector<pt> st;
    for (int i = 0; i < (int)a.size(); i++) {
        while (st.size() > 1 && !cw(st[st.size()-2], st.back(), a[i], include_collinear))
            st.pop_back();
        st.push_back(a[i]);
    }

    a = st;
}

```

> link to source code <https://cp-algorithms.com/geometry/convex-hull.html>

>LINK TO REPO <https://github.com/phani8493/assignment2-vangipurapu.git>