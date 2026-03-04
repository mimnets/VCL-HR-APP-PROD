PocketBase Collections to Create

 Collection: review_cycles

 ┌─────────────────────┬────────────────────────┬──────────┬──────────────────────────────────┐
 │        Field        │          Type          │ Required │              Notes               │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ name                │ Text                   │ Yes      │ e.g., "Mid-Year 2025"            │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ cycle_type          │ Select                 │ Yes      │ MID_YEAR, YEAR_END               │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ start_date          │ Date                   │ Yes      │ Review period start              │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ end_date            │ Date                   │ Yes      │ Review period end                │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ review_start_date   │ Date                   │ Yes      │ When submissions open            │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ review_end_date     │ Date                   │ Yes      │ Deadline for all reviews         │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ active_competencies │ JSON                   │ Yes      │ Array of CompetencyId strings    │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ is_active           │ Boolean                │ No       │ Only one active at a time        │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ status              │ Select                 │ Yes      │ UPCOMING, OPEN, CLOSED, ARCHIVED │
 ├─────────────────────┼────────────────────────┼──────────┼──────────────────────────────────┤
 │ organization_id     │ Relation→organizations │ Yes      │ Multi-tenancy                    │
 └─────────────────────┴────────────────────────┴──────────┴──────────────────────────────────┘

 API Rules: List/View by org_id, Create/Update/Delete restricted to ADMIN/HR

 Collection: performance_reviews

 Field: employee_id
 Type: Relation→users
 Required: Yes
 Notes:
 ────────────────────────────────────────
 Field: employee_name
 Type: Text
 Required: Yes
 Notes:
 ────────────────────────────────────────
 Field: cycle_id
 Type: Relation→review_cycles
 Required: Yes
 Notes:
 ────────────────────────────────────────
 Field: line_manager_id
 Type: Relation→users
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: manager_name
 Type: Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: status
 Type: Select
 Required: Yes
 Notes: DRAFT, SELF_REVIEW_SUBMITTED, MANAGER_REVIEWED, COMPLETED
 ────────────────────────────────────────
 Field: submitted_at
 Type: DateTime
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: manager_reviewed_at
 Type: DateTime
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: completed_at
 Type: DateTime
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: Self-assessment (12 fields)
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: self_agility_rating / self_agility_comment
 Type: Number / Text
 Required: No
 Notes: Repeat for all 6 competencies
 ────────────────────────────────────────
 Field: self_collaboration_rating / self_collaboration_comment
 Type: Number / Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: self_customer_focus_rating / self_customer_focus_comment
 Type: Number / Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: self_developing_others_rating / self_developing_others_comment
 Type: Number / Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: self_global_mindset_rating / self_global_mindset_comment
 Type: Number / Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: self_innovation_mindset_rating / self_innovation_mindset_comment
 Type: Number / Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: Manager assessment (12 fields)
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: manager_agility_rating / manager_agility_comment
 Type: Number / Text
 Required: No
 Notes: Repeat for all 6 competencies
 ────────────────────────────────────────
 Field: ... (same pattern as self)
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: Attendance summary
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: total_working_days / present_days / late_days / absent_days / early_out_days
 Type: Number
 Required: No
 Notes: Auto-calculated
 ────────────────────────────────────────
 Field: attendance_percentage
 Type: Number
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: Leave summary
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: annual_leave_taken / casual_leave_taken / sick_leave_taken
 Type: Number
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: unpaid_leave_taken / total_leave_days
 Type: Number
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: HR finalization
 Type:
 Required:
 Notes:
 ────────────────────────────────────────
 Field: hr_final_remarks
 Type: Text
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: hr_overall_rating
 Type: Select
 Required: No
 Notes: EXCELLENT → UNSATISFACTORY
 ────────────────────────────────────────
 Field: finalized_by
 Type: Relation→users
 Required: No
 Notes:
 ────────────────────────────────────────
 Field: organization_id
 Type: Relation→organizations
 Required: Yes
 Notes:

 API Rules: List/View by org_id, Create by employee or ADMIN/HR, Update by employee/manager/ADMIN/HR

 ---
 Attendance & Leave Integration

 When a review is created or opened:
 1. Get the cycle's start_date and end_date
 2. Attendance: Fetch via hrService.getAttendance(), filter by employee + date range, use consolidateAttendance() from    
 src/utils/attendanceUtils.ts, count PRESENT/LATE/ABSENT/EARLY_OUT, calculate working days from shift config + holidays   
 3. Leave: Fetch via hrService.getLeaves(), filter APPROVED leaves in date range, group by type, sum totalDays
 4. Store as snapshot on the performance_reviews record (frozen at submission time)

 ---
 Implementation Order

 1. Add types to src/types.ts
 2. Add competency constants to src/constants.tsx
 3. Create PocketBase collections (manual in PB admin console)
 4. Create src/services/review.service.ts with field mapping + CRUD + attendance/leave calculations
 5. Update src/services/hrService.ts facade
 6. Create src/hooks/review/usePerformanceReview.ts
 7. Create reusable components: ReviewStatusBadge, CompetencyRatingCard, AttendanceLeaveCard
 8. Create role modules: EmployeeReviewModule, ManagerReviewModule, HRReviewModule
 9. Create src/pages/PerformanceReview.tsx
 10. Update Sidebar.tsx (add menu item) and App.tsx (add route)
 11. Build, sync, and test

 ---
 Verification

 - Employee flow: Login as EMPLOYEE → navigate to Performance Review → see active cycle → fill all 6 competency
 self-ratings + comments → submit → verify status changes to SELF_REVIEW_SUBMITTED
 - Manager flow: Login as MANAGER → see direct reports' submitted reviews → add manager ratings/comments for each →       
 submit → verify MANAGER_REVIEWED status
 - Admin flow: Login as ADMIN → create a review cycle → verify all employees can see it → finalize completed reviews with 
  HR remarks + overall rating → verify COMPLETED status
 - Attendance/Leave: Verify attendance summary shows correct present/late/absent counts for the cycle period, and leave   
 summary shows correct type breakdown
 - Access control: Verify employees can't see others' reviews, managers only see direct reports, subscription read-only   
 mode blocks submissions
