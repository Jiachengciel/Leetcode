**描述**
==
Given a non-overlapping interval list which is sorted by start point.

Insert a new interval into it, make sure the list is still in order and non-overlapping (merge intervals if necessary).

**Example:**

Insert (2, 5) into [(1,2), (5,9)], we get [(1,9)].
Insert (3, 4) into [(1,2), (5,9)], we get [(1,2), (3,4), (5,9)].

**Code**
==
        /**
         * Definition of Interval:
         * classs Interval {
         *     int start, end;
         *     Interval(int start, int end) {
         *         this->start = start;
         *         this->end = end;
         *     }
         * }
         */

        class Solution {
        public:
            /**
             * @param intervals: Sorted interval list.
             * @param newInterval: new interval.
             * @return: A new interval list.
             */
            vector<Interval> insert(vector<Interval> &intervals, Interval newInterval) {
                vector<Interval> fin;
                for(auto element: intervals){
                    if(element.start>newInterval.end){
                        fin.push_back(newInterval);
                        newInterval = element;
                    }
                    else if(element.end<newInterval.start)
                        fin.push_back(element);
                    else{
                        int start_temp = std::min(element.start, newInterval.start);
                        int end_temp = std::max(element.end, newInterval.end);
                        newInterval = Interval(start_temp, end_temp);
                    }
                }
                fin.push_back(newInterval);
                return fin;
            }
        };
