#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        vector<int> temp;

        // Combine both arrays
        for (auto i : nums1)
            temp.push_back(i);
        for (auto i : nums2)
            temp.push_back(i);

        // Sort the combined array
        sort(temp.begin(), temp.end());
        int n = temp.size();
        double ans;

        // Check if the size is odd or even and calculate median
        if (n & 1) {
            ans = temp[n / 2];
        } else {
            ans = (temp[n / 2] + temp[n / 2 - 1]) / 2.0;
        }
        return ans;
    }
};

int main() {
    Solution sol;

    // Input first array
    int n1;
    cout << "Enter the size of the first array: ";
    cin >> n1;
    vector<int> nums1(n1);
    cout << "Enter the elements of the first array (sorted): ";
    for (int i = 0; i < n1; ++i) {
        cin >> nums1[i];
    }

    // Input second array
    int n2;
    cout << "Enter the size of the second array: ";
    cin >> n2;
    vector<int> nums2(n2);
    cout << "Enter the elements of the second array (sorted): ";
    for (int i = 0; i < n2; ++i) {
        cin >> nums2[i];
    }

    // Find and display the median
    double median = sol.findMedianSortedArrays(nums1, nums2);
    cout << "The median of the two sorted arrays is: " << median << endl;

    return 0;
}
