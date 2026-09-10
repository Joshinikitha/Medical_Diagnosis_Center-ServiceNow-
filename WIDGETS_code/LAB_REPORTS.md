# LAB\_REPORTS:

## **HTML**

<div class="lab-reports">



&#x20; <!-- HEADER -->

&#x20; <div class="rpt-header">

&#x20;   <div class="rpt-header-left">

&#x20;     <h1 class="rpt-title">📄 My Lab Reports</h1>

&#x20;     <p class="rpt-sub">View and download your diagnostic test results.</p>

&#x20;   </div>

&#x20;   <div class="rpt-header-right">

&#x20;     <button class="btn-back-home" ng-click="c.goHome()">

&#x20;       <i class="fa fa-home"></i> Home

&#x20;     </button>

&#x20;     <button class="btn-my-bookings" ng-click="c.goBookings()">

&#x20;       <i class="fa fa-calendar"></i> My Bookings

&#x20;     </button>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- STATS BAR -->

&#x20; <div class="rpt-stats-bar">

&#x20;   <div class="rpt-stat-card" ng-repeat="stat in c.stats">

&#x20;     <span class="rpt-stat-icon">{{stat.icon}}</span>

&#x20;     <div class="rpt-stat-info">

&#x20;       <span class="rpt-stat-val">{{stat.count}}</span>

&#x20;       <span class="rpt-stat-name">{{stat.label}}</span>

&#x20;     </div>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- SEARCH -->

&#x20; <div class="rpt-controls">

&#x20;   <div class="rpt-search-wrap">

&#x20;     <i class="fa fa-search"></i>

&#x20;     <input type="text" class="rpt-search" placeholder="Search by test name or report number..."

&#x20;       ng-model="c.searchQuery" ng-change="c.filterReports()" />

&#x20;   </div>

&#x20;   <select class="rpt-sort" ng-model="c.sortBy" ng-change="c.filterReports()">

&#x20;     <option value="date\_desc">Newest First</option>

&#x20;     <option value="date\_asc">Oldest First</option>

&#x20;     <option value="name">By Test Name</option>

&#x20;   </select>

&#x20; </div>



&#x20; <!-- LOADING -->

&#x20; <div class="rpt-loading" ng-if="c.loading">

&#x20;   <div class="spinner-ring"></div>

&#x20;   <p>Loading your reports...</p>

&#x20; </div>



&#x20; <!-- EMPTY STATE -->

&#x20; <div class="rpt-empty" ng-if="!c.loading \&\& c.filteredReports.length === 0">

&#x20;   <div class="rpt-empty-icon">📭</div>

&#x20;   <h3>No reports found</h3>

&#x20;   <p ng-if="c.searchQuery">No reports match your search.</p>

&#x20;   <p ng-if="!c.searchQuery">Your lab reports will appear here once they are uploaded by the diagnostic center.</p>

&#x20;   <button class="btn-book-test" ng-click="c.goHome()">Browse Tests</button>

&#x20; </div>



&#x20; <!-- REPORTS LIST -->

&#x20; <div class="rpt-list" ng-if="!c.loading \&\& c.filteredReports.length > 0">

&#x20;   <div class="rpt-card" ng-repeat="report in c.filteredReports">



&#x20;     <!-- STATUS BAR -->

&#x20;     <div class="rpt-card-accent" ng-style="{'background': c.getStatusColor(report.status)}"></div>



&#x20;     <div class="rpt-card-content">

&#x20;       <!-- TOP ROW -->

&#x20;       <div class="rpt-card-top">

&#x20;         <div class="rpt-card-title-group">

&#x20;           <span class="rpt-icon">{{c.getCategoryIcon(report.test\_category)}}</span>

&#x20;           <div>

&#x20;             <h3 class="rpt-test-name" ng-bind="report.test\_name"></h3>

&#x20;             <span class="rpt-number" ng-bind="report.report\_number"></span>

&#x20;           </div>

&#x20;         </div>

&#x20;         <div class="rpt-status-wrap">

&#x20;           <span class="rpt-status-pill"

&#x20;             ng-style="{'background': c.getStatusBg(report.status), 'color': c.getStatusColor(report.status)}">

&#x20;             {{c.getStatusLabel(report.status)}}

&#x20;           </span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- META -->

&#x20;       <div class="rpt-meta">

&#x20;         <div class="rpt-meta-chip">

&#x20;           <i class="fa fa-calendar"></i>

&#x20;           <span>Test Date: {{report.test\_date\_display || 'N/A'}}</span>

&#x20;         </div>

&#x20;         <div class="rpt-meta-chip">

&#x20;           <i class="fa fa-clock-o"></i>

&#x20;           <span>Report Date: {{report.report\_date\_display || 'N/A'}}</span>

&#x20;         </div>

&#x20;         <div class="rpt-meta-chip" ng-if="report.doctor\_name">

&#x20;           <i class="fa fa-user-md"></i>

&#x20;           <span>Dr. {{report.doctor\_name}}</span>

&#x20;         </div>

&#x20;         <div class="rpt-meta-chip" ng-if="report.test\_category">

&#x20;           <i class="fa fa-tag"></i>

&#x20;           <span>{{report.test\_category}}</span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <!-- SUMMARY / FINDINGS — rendered as rich HTML -->

&#x20;       <div class="rpt-findings" ng-if="report.findings">

&#x20;         <div class="rpt-findings-label"><i class="fa fa-file-text-o"></i> Findings</div>

&#x20;         <div class="rpt-findings-body" ng-bind-html="report.findings"></div>

&#x20;       </div>



&#x20;       <!-- REMARKS -->

&#x20;       <div class="rpt-remarks" ng-if="report.remarks">

&#x20;         <i class="fa fa-comment-o"></i> <em ng-bind="report.remarks"></em>

&#x20;       </div>



&#x20;       <!-- ACTIONS -->

&#x20;       <div class="rpt-actions">

&#x20;         <button class="rpt-btn btn-view-detail" ng-click="c.viewDetail(report)">

&#x20;           <i class="fa fa-eye"></i> View Details

&#x20;         </button>

&#x20;         <button class="rpt-btn btn-download" ng-if="report.report\_url" ng-click="c.downloadReport(report)">

&#x20;           <i class="fa fa-download"></i> Download Report

&#x20;         </button>

&#x20;         <span class="rpt-appt-link" ng-if="report.appointment\_number">

&#x20;           Booking: <strong ng-bind="report.appointment\_number"></strong>

&#x20;         </span>

&#x20;       </div>

&#x20;     </div>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- DETAIL MODAL -->

&#x20; <div class="rpt-modal-overlay" ng-if="c.showModal" ng-click="c.closeModal()">

&#x20;   <div class="rpt-modal-box" ng-click="$event.stopPropagation()">

&#x20;     <div class="rpt-modal-header">

&#x20;       <h3>Report Details</h3>

&#x20;       <button class="rpt-modal-close" ng-click="c.closeModal()">✕</button>

&#x20;     </div>

&#x20;     <div class="rpt-modal-body" ng-if="c.selectedReport">

&#x20;       <div class="rpt-detail-grid">

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Report #</span>

&#x20;           <span class="rpt-detail-val mono" ng-bind="c.selectedReport.report\_number"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Status</span>

&#x20;           <span class="rpt-detail-val">

&#x20;             <span class="rpt-status-pill"

&#x20;               ng-style="{'background': c.getStatusBg(c.selectedReport.status), 'color': c.getStatusColor(c.selectedReport.status)}">

&#x20;               {{c.getStatusLabel(c.selectedReport.status)}}

&#x20;             </span>

&#x20;           </span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Test Name</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.test\_name"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Category</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.test\_category"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Test Date</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.test\_date\_display"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Report Date</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.report\_date\_display"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Doctor</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.doctor\_name || 'N/A'"></span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item">

&#x20;           <span class="rpt-detail-key">Appointment #</span>

&#x20;           <span class="rpt-detail-val mono" ng-bind="c.selectedReport.appointment\_number || 'N/A'"></span>

&#x20;         </div>

&#x20;         <!-- Findings rendered as rich HTML in modal -->

&#x20;         <div class="rpt-detail-item full">

&#x20;           <span class="rpt-detail-key">Findings</span>

&#x20;           <div class="rpt-modal-findings" ng-if="c.selectedReport.findings" ng-bind-html="c.selectedReport.findings"></div>

&#x20;           <span class="rpt-detail-val" ng-if="!c.selectedReport.findings">None</span>

&#x20;         </div>

&#x20;         <div class="rpt-detail-item full">

&#x20;           <span class="rpt-detail-key">Remarks</span>

&#x20;           <span class="rpt-detail-val" ng-bind="c.selectedReport.remarks || 'None'"></span>

&#x20;         </div>

&#x20;       </div>

&#x20;     </div>

&#x20;     <div class="rpt-modal-footer">

&#x20;       <button class="rpt-btn btn-download"

&#x20;         ng-if="c.selectedReport \&\& c.selectedReport.report\_url"

&#x20;         ng-click="c.downloadReport(c.selectedReport)">

&#x20;         <i class="fa fa-download"></i> Download Report

&#x20;       </button>

&#x20;       <button class="rpt-btn btn-close-modal" ng-click="c.closeModal()">Close</button>

&#x20;     </div>

&#x20;   </div>

&#x20; </div>



</div>



#### **CSS**

/\* =========================================================

&#x20;  MEDICA — LAB REPORTS

&#x20;  Clean clinical dashboard / professional UI

&#x20;  ========================================================= \*/



.lab-reports {

&#x20; --navy: #12345b;

&#x20; --navy-dark: #0d2948;

&#x20; --blue: #1677c8;

&#x20; --cyan: #12a9c7;

&#x20; --green: #15966d;

&#x20; --amber: #c98216;

&#x20; --red: #c94a4a;



&#x20; --text: #243447;

&#x20; --text-soft: #617286;

&#x20; --text-muted: #8b9aaa;



&#x20; --bg: #f5f8fb;

&#x20; --surface: #ffffff;

&#x20; --surface-soft: #f8fafc;

&#x20; --border: #e3eaf1;

&#x20; --border-light: #edf1f5;



&#x20; --shadow-xs: 0 1px 2px rgba(18, 52, 91, 0.04);

&#x20; --shadow-sm: 0 3px 12px rgba(18, 52, 91, 0.06);

&#x20; --shadow-md: 0 10px 28px rgba(18, 52, 91, 0.09);

&#x20; --shadow-lg: 0 20px 55px rgba(18, 52, 91, 0.16);



&#x20; font-family: "Segoe UI", Inter, Arial, sans-serif;

&#x20; background: var(--bg);

&#x20; color: var(--text);

&#x20; min-height: 100vh;

&#x20; padding-bottom: 70px;

}





/\* =========================================================

&#x20;  HEADER

&#x20;  ========================================================= \*/



.rpt-header {

&#x20; position: relative;

&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: space-between;

&#x20; gap: 30px;



&#x20; padding: 42px 44px 46px;



&#x20; background:

&#x20;   linear-gradient(

&#x20;     120deg,

&#x20;     #102f52 0%,

&#x20;     #164875 58%,

&#x20;     #126b89 100%

&#x20;   );



&#x20; border-radius: 0 0 28px 28px;

&#x20; overflow: hidden;

}



/\* subtle decorative background \*/

.rpt-header::before {

&#x20; content: "";

&#x20; position: absolute;

&#x20; width: 360px;

&#x20; height: 360px;

&#x20; right: -150px;

&#x20; top: -190px;

&#x20; border-radius: 50%;

&#x20; border: 1px solid rgba(255,255,255,0.08);

&#x20; box-shadow:

&#x20;   0 0 0 40px rgba(255,255,255,0.025),

&#x20;   0 0 0 80px rgba(255,255,255,0.018);

}



.rpt-header::after {

&#x20; content: "";

&#x20; position: absolute;

&#x20; width: 160px;

&#x20; height: 160px;

&#x20; right: 150px;

&#x20; bottom: -110px;

&#x20; border-radius: 50%;

&#x20; background: rgba(18,169,199,0.08);

}



.rpt-header-left,

.rpt-header-right {

&#x20; position: relative;

&#x20; z-index: 2;

}



.rpt-title {

&#x20; margin: 0 0 9px;



&#x20; color: #ffffff;

&#x20; font-size: 31px;

&#x20; font-weight: 700;

&#x20; line-height: 1.2;

&#x20; letter-spacing: -0.4px;

}



.rpt-sub {

&#x20; margin: 0;

&#x20; color: rgba(255,255,255,0.72);

&#x20; font-size: 14px;

&#x20; line-height: 1.6;

}



.rpt-header-right {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 10px;

}





/\* =========================================================

&#x20;  HEADER BUTTONS

&#x20;  ========================================================= \*/



.btn-back-home,

.btn-my-bookings {

&#x20; display: inline-flex;

&#x20; align-items: center;

&#x20; justify-content: center;

&#x20; gap: 8px;



&#x20; min-height: 40px;

&#x20; padding: 0 17px;



&#x20; border-radius: 8px;



&#x20; font-size: 13px;

&#x20; font-weight: 600;



&#x20; cursor: pointer;

&#x20; transition:

&#x20;   transform 0.22s ease,

&#x20;   background 0.22s ease,

&#x20;   border-color 0.22s ease,

&#x20;   box-shadow 0.22s ease;

}



.btn-back-home {

&#x20; color: #ffffff;

&#x20; background: rgba(255,255,255,0.08);

&#x20; border: 1px solid rgba(255,255,255,0.22);

}



.btn-back-home:hover {

&#x20; background: rgba(255,255,255,0.15);

&#x20; border-color: rgba(255,255,255,0.35);

&#x20; transform: translateY(-1px);

}



.btn-my-bookings {

&#x20; color: #ffffff;

&#x20; background: #13a9c7;

&#x20; border: 1px solid #13a9c7;

&#x20; box-shadow: 0 5px 15px rgba(18,169,199,0.25);

}



.btn-my-bookings:hover {

&#x20; background: #0f95b1;

&#x20; border-color: #0f95b1;

&#x20; transform: translateY(-1px);

&#x20; box-shadow: 0 8px 20px rgba(18,169,199,0.3);

}



.btn-back-home:active,

.btn-my-bookings:active {

&#x20; transform: translateY(0);

}





/\* =========================================================

&#x20;  STATS

&#x20;  ========================================================= \*/



.rpt-stats-bar {

&#x20; display: grid;

&#x20; grid-template-columns: repeat(4, minmax(0, 1fr));

&#x20; gap: 14px;



&#x20; padding: 24px 44px 0;

}



.rpt-stat-card {

&#x20; position: relative;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 14px;



&#x20; min-height: 82px;

&#x20; padding: 17px 18px;



&#x20; background: var(--surface);

&#x20; border: 1px solid var(--border);

&#x20; border-radius: 11px;



&#x20; box-shadow: var(--shadow-xs);



&#x20; transition:

&#x20;   transform 0.24s ease,

&#x20;   box-shadow 0.24s ease,

&#x20;   border-color 0.24s ease;

}



.rpt-stat-card::after {

&#x20; content: "";

&#x20; position: absolute;

&#x20; left: 0;

&#x20; top: 18px;

&#x20; bottom: 18px;

&#x20; width: 3px;



&#x20; border-radius: 0 3px 3px 0;

&#x20; background: var(--cyan);



&#x20; opacity: 0.7;

}



.rpt-stat-card:hover {

&#x20; transform: translateY(-2px);

&#x20; border-color: #d7e2ec;

&#x20; box-shadow: var(--shadow-md);

}



.rpt-stat-icon {

&#x20; width: 42px;

&#x20; height: 42px;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border-radius: 9px;



&#x20; background: #edf7fa;

&#x20; color: var(--cyan);



&#x20; font-size: 21px;

}



.rpt-stat-info {

&#x20; display: flex;

&#x20; flex-direction: column;

&#x20; gap: 4px;

}



.rpt-stat-val {

&#x20; color: var(--navy);

&#x20; font-size: 23px;

&#x20; font-weight: 700;

&#x20; line-height: 1;

}



.rpt-stat-name {

&#x20; color: var(--text-muted);

&#x20; font-size: 11px;

&#x20; font-weight: 600;

&#x20; text-transform: uppercase;

&#x20; letter-spacing: 0.45px;

}





/\* =========================================================

&#x20;  SEARCH / CONTROLS

&#x20;  ========================================================= \*/



.rpt-controls {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 10px;



&#x20; padding: 25px 44px 15px;

}



.rpt-search-wrap {

&#x20; position: relative;

&#x20; width: 100%;

&#x20; max-width: 430px;

}



.rpt-search-wrap .fa {

&#x20; position: absolute;

&#x20; left: 14px;

&#x20; top: 50%;



&#x20; transform: translateY(-50%);



&#x20; color: #98a7b6;

&#x20; font-size: 13px;



&#x20; transition: color 0.2s ease;

}



.rpt-search {

&#x20; width: 100%;

&#x20; height: 42px;



&#x20; box-sizing: border-box;



&#x20; padding: 0 15px 0 38px;



&#x20; background: var(--surface);

&#x20; border: 1px solid var(--border);

&#x20; border-radius: 8px;



&#x20; color: var(--text);

&#x20; font-size: 13px;



&#x20; outline: none;



&#x20; box-shadow: var(--shadow-xs);



&#x20; transition:

&#x20;   border-color 0.22s ease,

&#x20;   box-shadow 0.22s ease;

}



.rpt-search::placeholder {

&#x20; color: #a0adba;

}



.rpt-search:hover {

&#x20; border-color: #ccd8e3;

}



.rpt-search:focus {

&#x20; border-color: var(--cyan);

&#x20; box-shadow:

&#x20;   0 0 0 3px rgba(18,169,199,0.10);

}



.rpt-search:focus + \* {

&#x20; color: var(--cyan);

}



.rpt-search-wrap:focus-within .fa {

&#x20; color: var(--cyan);

}



.rpt-sort {

&#x20; height: 42px;



&#x20; padding: 0 35px 0 13px;



&#x20; background: var(--surface);

&#x20; border: 1px solid var(--border);

&#x20; border-radius: 8px;



&#x20; color: var(--text-soft);

&#x20; font-size: 13px;



&#x20; cursor: pointer;

&#x20; outline: none;



&#x20; transition:

&#x20;   border-color 0.22s ease,

&#x20;   box-shadow 0.22s ease;

}



.rpt-sort:hover {

&#x20; border-color: #ccd8e3;

}



.rpt-sort:focus {

&#x20; border-color: var(--cyan);

&#x20; box-shadow: 0 0 0 3px rgba(18,169,199,0.10);

}





/\* =========================================================

&#x20;  LOADING

&#x20;  ========================================================= \*/



.rpt-loading {

&#x20; text-align: center;

&#x20; padding: 75px 20px;

&#x20; color: var(--text-soft);

}



.rpt-loading p {

&#x20; margin: 10px 0 0;

&#x20; font-size: 13px;

}



.spinner-ring {

&#x20; display: inline-block;



&#x20; width: 34px;

&#x20; height: 34px;



&#x20; border: 3px solid #dfe7ee;

&#x20; border-top-color: var(--cyan);



&#x20; border-radius: 50%;



&#x20; animation: rptSpin 0.75s linear infinite;

}



@keyframes rptSpin {

&#x20; to {

&#x20;   transform: rotate(360deg);

&#x20; }

}





/\* =========================================================

&#x20;  EMPTY STATE

&#x20;  ========================================================= \*/



.rpt-empty {

&#x20; max-width: 560px;

&#x20; margin: 35px auto;

&#x20; padding: 55px 30px;



&#x20; text-align: center;



&#x20; background: var(--surface);

&#x20; border: 1px solid var(--border);

&#x20; border-radius: 14px;



&#x20; box-shadow: var(--shadow-sm);

}



.rpt-empty-icon {

&#x20; width: 64px;

&#x20; height: 64px;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; margin: 0 auto 17px;



&#x20; border-radius: 50%;

&#x20; background: #eef7fa;



&#x20; font-size: 30px;

}



.rpt-empty h3 {

&#x20; margin: 0 0 7px;



&#x20; color: var(--navy);

&#x20; font-size: 19px;

&#x20; font-weight: 700;

}



.rpt-empty p {

&#x20; max-width: 430px;

&#x20; margin: 0 auto 22px;



&#x20; color: var(--text-soft);

&#x20; font-size: 13px;

&#x20; line-height: 1.7;

}



.btn-book-test {

&#x20; min-height: 40px;



&#x20; padding: 0 22px;



&#x20; color: #ffffff;

&#x20; background: var(--navy);



&#x20; border: 0;

&#x20; border-radius: 8px;



&#x20; font-size: 13px;

&#x20; font-weight: 600;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   background 0.22s ease,

&#x20;   transform 0.22s ease,

&#x20;   box-shadow 0.22s ease;

}



.btn-book-test:hover {

&#x20; background: var(--navy-dark);

&#x20; transform: translateY(-1px);

&#x20; box-shadow: 0 6px 15px rgba(18,52,91,0.18);

}





/\* =========================================================

&#x20;  REPORT LIST

&#x20;  ========================================================= \*/



.rpt-list {

&#x20; display: flex;

&#x20; flex-direction: column;

&#x20; gap: 13px;



&#x20; padding: 10px 44px;

}





/\* =========================================================

&#x20;  REPORT CARD

&#x20;  ========================================================= \*/



.rpt-card {

&#x20; position: relative;



&#x20; display: flex;



&#x20; background: var(--surface);



&#x20; border: 1px solid var(--border);

&#x20; border-radius: 11px;



&#x20; overflow: hidden;



&#x20; box-shadow: var(--shadow-xs);



&#x20; transition:

&#x20;   transform 0.25s ease,

&#x20;   box-shadow 0.25s ease,

&#x20;   border-color 0.25s ease;

}



.rpt-card:hover {

&#x20; transform: translateY(-2px);



&#x20; border-color: #d6e1eb;



&#x20; box-shadow: var(--shadow-md);

}



.rpt-card-accent {

&#x20; width: 4px;

&#x20; flex-shrink: 0;

}



.rpt-card-content {

&#x20; flex: 1;

&#x20; min-width: 0;

&#x20; padding: 19px 22px 18px;

}





/\* =========================================================

&#x20;  REPORT TOP

&#x20;  ========================================================= \*/



.rpt-card-top {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: space-between;



&#x20; gap: 20px;



&#x20; margin-bottom: 15px;

}



.rpt-card-title-group {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 13px;



&#x20; min-width: 0;

}



.rpt-icon {

&#x20; width: 43px;

&#x20; height: 43px;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; flex-shrink: 0;



&#x20; background: #eef7fa;

&#x20; border: 1px solid #dceef2;

&#x20; border-radius: 9px;



&#x20; font-size: 20px;

}



.rpt-test-name {

&#x20; margin: 0 0 4px;



&#x20; color: var(--navy);

&#x20; font-size: 16px;

&#x20; font-weight: 700;



&#x20; line-height: 1.3;

}



.rpt-number {

&#x20; color: var(--text-muted);

&#x20; font-family: "Courier New", monospace;

&#x20; font-size: 11px;

&#x20; letter-spacing: 0.2px;

}



.rpt-status-wrap {

&#x20; flex-shrink: 0;

}



.rpt-status-pill {

&#x20; display: inline-flex;

&#x20; align-items: center;



&#x20; min-height: 27px;

&#x20; padding: 0 11px;



&#x20; border-radius: 20px;



&#x20; font-size: 11px;

&#x20; font-weight: 700;



&#x20; white-space: nowrap;

}





/\* =========================================================

&#x20;  META INFORMATION

&#x20;  ========================================================= \*/



.rpt-meta {

&#x20; display: flex;

&#x20; flex-wrap: wrap;

&#x20; gap: 8px;



&#x20; padding-bottom: 15px;



&#x20; border-bottom: 1px solid var(--border-light);

}



.rpt-meta-chip {

&#x20; display: inline-flex;

&#x20; align-items: center;

&#x20; gap: 6px;



&#x20; padding: 6px 9px;



&#x20; background: var(--surface-soft);

&#x20; border: 1px solid var(--border-light);

&#x20; border-radius: 6px;



&#x20; color: var(--text-soft);



&#x20; font-size: 11.5px;



&#x20; transition:

&#x20;   background 0.2s ease,

&#x20;   border-color 0.2s ease;

}



.rpt-meta-chip:hover {

&#x20; background: #f2f7fa;

&#x20; border-color: #dfe8ef;

}



.rpt-meta-chip .fa {

&#x20; color: var(--cyan);

&#x20; font-size: 11px;

}





/\* =========================================================

&#x20;  FINDINGS

&#x20;  ========================================================= \*/



.rpt-findings {

&#x20; margin-top: 15px;

&#x20; margin-bottom: 13px;



&#x20; padding: 13px 15px;



&#x20; background: #f8fbfd;



&#x20; border: 1px solid #e5eef3;

&#x20; border-left: 3px solid var(--cyan);



&#x20; border-radius: 0 8px 8px 0;



&#x20; overflow-x: auto;

}



.rpt-findings-label {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 7px;



&#x20; margin-bottom: 9px;



&#x20; color: var(--navy);



&#x20; font-size: 10px;

&#x20; font-weight: 700;



&#x20; text-transform: uppercase;

&#x20; letter-spacing: 0.65px;

}



.rpt-findings-label .fa {

&#x20; color: var(--cyan);

}



.rpt-findings-body {

&#x20; color: var(--text-soft);

&#x20; font-size: 12.5px;

&#x20; line-height: 1.6;

}



.rpt-findings-body h3 {

&#x20; margin: 0 0 9px;



&#x20; padding-bottom: 7px;



&#x20; color: var(--navy);



&#x20; border-bottom: 1px solid #dce8ef;



&#x20; font-size: 14px;

&#x20; font-weight: 700;

}



.rpt-findings-body p {

&#x20; margin: 6px 0;

&#x20; color: var(--text-soft);

&#x20; font-size: 12.5px;

}



.rpt-findings-body strong {

&#x20; color: var(--text);

}





/\* =========================================================

&#x20;  FINDINGS TABLE

&#x20;  ========================================================= \*/



.rpt-findings-body table,

.rpt-modal-findings table {

&#x20; width: 100%;



&#x20; border-collapse: separate;

&#x20; border-spacing: 0;



&#x20; margin: 8px 0;



&#x20; background: #ffffff;



&#x20; border: 1px solid var(--border);

&#x20; border-radius: 7px;



&#x20; overflow: hidden;



&#x20; font-size: 12px;

}



.rpt-findings-body table thead tr,

.rpt-modal-findings table thead tr {

&#x20; background: #f1f6fa;

&#x20; color: var(--navy);

}



.rpt-findings-body table th,

.rpt-modal-findings table th {

&#x20; padding: 9px 12px;



&#x20; text-align: left;



&#x20; font-size: 11px;

&#x20; font-weight: 700;



&#x20; border-bottom: 1px solid #dfe8ef;

}



.rpt-findings-body table td,

.rpt-modal-findings table td {

&#x20; padding: 8px 12px;



&#x20; color: var(--text-soft);



&#x20; border-bottom: 1px solid var(--border-light);

}



.rpt-findings-body table tbody tr:last-child td,

.rpt-modal-findings table tbody tr:last-child td {

&#x20; border-bottom: none;

}



.rpt-findings-body table tbody tr,

.rpt-modal-findings table tbody tr {

&#x20; transition: background 0.18s ease;

}



.rpt-findings-body table tbody tr:hover,

.rpt-modal-findings table tbody tr:hover {

&#x20; background: #f7fbfd;

}



.rpt-findings-body td:last-child,

.rpt-modal-findings td:last-child {

&#x20; font-weight: 700;

}





/\* =========================================================

&#x20;  REMARKS

&#x20;  ========================================================= \*/



.rpt-remarks {

&#x20; display: flex;

&#x20; align-items: flex-start;

&#x20; gap: 8px;



&#x20; margin-bottom: 13px;

&#x20; padding: 8px 11px;



&#x20; background: #fafbfc;



&#x20; border-left: 2px solid #d9e1e8;

&#x20; border-radius: 0 6px 6px 0;



&#x20; color: var(--text-soft);



&#x20; font-size: 12px;

&#x20; line-height: 1.5;

}



.rpt-remarks .fa {

&#x20; margin-top: 2px;

&#x20; color: #8998a7;

}





/\* =========================================================

&#x20;  ACTIONS

&#x20;  ========================================================= \*/



.rpt-actions {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; flex-wrap: wrap;

&#x20; gap: 8px;

}



.rpt-btn {

&#x20; display: inline-flex;

&#x20; align-items: center;

&#x20; justify-content: center;

&#x20; gap: 7px;



&#x20; min-height: 34px;

&#x20; padding: 0 13px;



&#x20; border-radius: 7px;

&#x20; border: 1px solid transparent;



&#x20; font-size: 12px;

&#x20; font-weight: 600;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   transform 0.2s ease,

&#x20;   background 0.2s ease,

&#x20;   border-color 0.2s ease,

&#x20;   box-shadow 0.2s ease;

}



.rpt-btn:hover {

&#x20; transform: translateY(-1px);

}



.rpt-btn:active {

&#x20; transform: translateY(0);

}





/\* View button \*/

.btn-view-detail {

&#x20; color: #1765a0;

&#x20; background: #eef6fc;

&#x20; border-color: #d9e9f5;

}



.btn-view-detail:hover {

&#x20; background: #e2f0fa;

&#x20; border-color: #c7deed;

}





/\* Download button \*/

.btn-download {

&#x20; color: #147354;

&#x20; background: #eef8f4;

&#x20; border-color: #d7eee5;

}



.btn-download:hover {

&#x20; background: #e2f3ec;

&#x20; border-color: #c5e5d8;

}





/\* Close \*/

.btn-close-modal {

&#x20; color: #ffffff;

&#x20; background: var(--navy);

&#x20; border-color: var(--navy);

}



.btn-close-modal:hover {

&#x20; background: var(--navy-dark);

}



.rpt-appt-link {

&#x20; margin-left: auto;



&#x20; color: var(--text-muted);



&#x20; font-size: 11px;

}



.rpt-appt-link strong {

&#x20; color: var(--text-soft);

&#x20; font-weight: 600;

}





/\* =========================================================

&#x20;  MODAL

&#x20;  ========================================================= \*/



.rpt-modal-overlay {

&#x20; position: fixed;

&#x20; inset: 0;



&#x20; z-index: 9999;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; padding: 20px;



&#x20; background: rgba(13,41,72,0.48);



&#x20; backdrop-filter: blur(3px);



&#x20; animation: overlayIn 0.2s ease;

}



@keyframes overlayIn {

&#x20; from {

&#x20;   opacity: 0;

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20; }

}



.rpt-modal-box {

&#x20; width: 100%;

&#x20; max-width: 700px;

&#x20; max-height: 90vh;



&#x20; display: flex;

&#x20; flex-direction: column;



&#x20; background: #ffffff;



&#x20; border: 1px solid rgba(255,255,255,0.7);

&#x20; border-radius: 14px;



&#x20; overflow: hidden;



&#x20; box-shadow: var(--shadow-lg);



&#x20; animation: modalIn 0.28s cubic-bezier(.2,.8,.2,1);

}



@keyframes modalIn {

&#x20; from {

&#x20;   opacity: 0;

&#x20;   transform: translateY(14px) scale(0.985);

&#x20; }



&#x20; to {

&#x20;   opacity: 1;

&#x20;   transform: translateY(0) scale(1);

&#x20; }

}





/\* Modal header \*/



.rpt-modal-header {

&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: space-between;



&#x20; padding: 17px 21px;



&#x20; background: var(--navy);



&#x20; color: #ffffff;



&#x20; flex-shrink: 0;

}



.rpt-modal-header h3 {

&#x20; margin: 0;



&#x20; font-size: 16px;

&#x20; font-weight: 700;

}



.rpt-modal-close {

&#x20; width: 32px;

&#x20; height: 32px;



&#x20; display: flex;

&#x20; align-items: center;

&#x20; justify-content: center;



&#x20; border: 1px solid rgba(255,255,255,0.15);

&#x20; border-radius: 7px;



&#x20; background: rgba(255,255,255,0.07);

&#x20; color: #ffffff;



&#x20; font-size: 17px;



&#x20; cursor: pointer;



&#x20; transition:

&#x20;   background 0.2s ease,

&#x20;   transform 0.2s ease;

}



.rpt-modal-close:hover {

&#x20; background: rgba(255,255,255,0.16);

&#x20; transform: rotate(3deg);

}





/\* Modal body \*/



.rpt-modal-body {

&#x20; flex: 1;



&#x20; padding: 24px;



&#x20; overflow-y: auto;

}



.rpt-modal-body::-webkit-scrollbar {

&#x20; width: 6px;

}



.rpt-modal-body::-webkit-scrollbar-track {

&#x20; background: transparent;

}



.rpt-modal-body::-webkit-scrollbar-thumb {

&#x20; background: #ccd7e1;

&#x20; border-radius: 10px;

}





/\* Modal footer \*/



.rpt-modal-footer {

&#x20; display: flex;

&#x20; justify-content: flex-end;

&#x20; gap: 9px;



&#x20; padding: 14px 21px;



&#x20; border-top: 1px solid var(--border-light);



&#x20; background: #fbfcfd;



&#x20; flex-shrink: 0;

}





/\* =========================================================

&#x20;  DETAIL GRID

&#x20;  ========================================================= \*/



.rpt-detail-grid {

&#x20; display: grid;

&#x20; grid-template-columns: 1fr 1fr;

&#x20; gap: 0;



&#x20; border: 1px solid var(--border);

&#x20; border-radius: 9px;



&#x20; overflow: hidden;

}



.rpt-detail-item {

&#x20; display: flex;

&#x20; flex-direction: column;

&#x20; gap: 5px;



&#x20; min-height: 66px;



&#x20; padding: 13px 15px;



&#x20; background: #ffffff;



&#x20; border-bottom: 1px solid var(--border-light);

}



.rpt-detail-item:nth-child(odd) {

&#x20; border-right: 1px solid var(--border-light);

}



.rpt-detail-item.full {

&#x20; grid-column: 1 / -1;

&#x20; border-right: none;

}



.rpt-detail-key {

&#x20; color: var(--text-muted);



&#x20; font-size: 9.5px;

&#x20; font-weight: 700;



&#x20; text-transform: uppercase;

&#x20; letter-spacing: 0.6px;

}



.rpt-detail-val {

&#x20; color: var(--text);



&#x20; font-size: 13px;

&#x20; font-weight: 600;



&#x20; line-height: 1.5;

}



.rpt-detail-val.mono {

&#x20; color: var(--navy);

&#x20; font-family: "Courier New", monospace;

&#x20; font-size: 12px;

}



.rpt-modal-findings {

&#x20; margin-top: 4px;



&#x20; color: var(--text-soft);



&#x20; font-size: 12.5px;

&#x20; line-height: 1.6;



&#x20; overflow-x: auto;

}



.rpt-modal-findings h3 {

&#x20; margin: 0 0 9px;



&#x20; color: var(--navy);



&#x20; font-size: 14px;

&#x20; font-weight: 700;

}



.rpt-modal-findings p {

&#x20; margin: 6px 0;

}





/\* =========================================================

&#x20;  ACCESSIBILITY / FOCUS

&#x20;  ========================================================= \*/



.rpt-btn:focus-visible,

.btn-back-home:focus-visible,

.btn-my-bookings:focus-visible,

.btn-book-test:focus-visible,

.rpt-modal-close:focus-visible,

.rpt-search:focus-visible,

.rpt-sort:focus-visible {

&#x20; outline: 2px solid var(--cyan);

&#x20; outline-offset: 2px;

}





/\* =========================================================

&#x20;  RESPONSIVE

&#x20;  ========================================================= \*/



@media (max-width: 1000px) {



&#x20; .rpt-stats-bar {

&#x20;   grid-template-columns: repeat(2, 1fr);

&#x20; }



}





@media (max-width: 768px) {



&#x20; .rpt-header {

&#x20;   padding: 30px 20px 34px;

&#x20;   align-items: flex-start;

&#x20;   flex-direction: column;

&#x20;   border-radius: 0 0 22px 22px;

&#x20; }



&#x20; .rpt-title {

&#x20;   font-size: 26px;

&#x20; }



&#x20; .rpt-header-right {

&#x20;   width: 100%;

&#x20; }



&#x20; .btn-back-home,

&#x20; .btn-my-bookings {

&#x20;   flex: 1;

&#x20; }



&#x20; .rpt-stats-bar {

&#x20;   grid-template-columns: 1fr 1fr;

&#x20;   padding-left: 16px;

&#x20;   padding-right: 16px;

&#x20;   gap: 10px;

&#x20; }



&#x20; .rpt-stat-card {

&#x20;   padding: 14px;

&#x20; }



&#x20; .rpt-controls {

&#x20;   padding-left: 16px;

&#x20;   padding-right: 16px;

&#x20; }



&#x20; .rpt-search-wrap {

&#x20;   max-width: none;

&#x20; }



&#x20; .rpt-list {

&#x20;   padding-left: 16px;

&#x20;   padding-right: 16px;

&#x20; }



&#x20; .rpt-card-top {

&#x20;   align-items: flex-start;

&#x20;   flex-direction: column;

&#x20;   gap: 10px;

&#x20; }



&#x20; .rpt-status-wrap {

&#x20;   padding-left: 56px;

&#x20; }



&#x20; .rpt-detail-grid {

&#x20;   grid-template-columns: 1fr;

&#x20; }



&#x20; .rpt-detail-item:nth-child(odd) {

&#x20;   border-right: none;

&#x20; }



&#x20; .rpt-detail-item.full {

&#x20;   grid-column: auto;

&#x20; }



&#x20; .rpt-modal-box {

&#x20;   max-height: 94vh;

&#x20; }



}





@media (max-width: 520px) {



&#x20; .rpt-stats-bar {

&#x20;   grid-template-columns: 1fr;

&#x20; }



&#x20; .rpt-stat-card {

&#x20;   min-height: 68px;

&#x20; }



&#x20; .rpt-controls {

&#x20;   align-items: stretch;

&#x20;   flex-direction: column;

&#x20; }



&#x20; .rpt-sort {

&#x20;   width: 100%;

&#x20; }



&#x20; .rpt-card-content {

&#x20;   padding: 16px;

&#x20; }



&#x20; .rpt-meta-chip {

&#x20;   width: 100%;

&#x20; }



&#x20; .rpt-actions {

&#x20;   align-items: stretch;

&#x20; }



&#x20; .rpt-btn {

&#x20;   flex: 1;

&#x20; }



&#x20; .rpt-appt-link {

&#x20;   width: 100%;

&#x20;   margin-left: 0;

&#x20;   margin-top: 3px;

&#x20; }



&#x20; .rpt-modal-overlay {

&#x20;   padding: 10px;

&#x20; }



&#x20; .rpt-modal-body {

&#x20;   padding: 16px;

&#x20; }



}





/\* =========================================================

&#x20;  REDUCED MOTION

&#x20;  ========================================================= \*/



@media (prefers-reduced-motion: reduce) {



&#x20; .lab-reports \*,

&#x20; .lab-reports \*::before,

&#x20; .lab-reports \*::after {

&#x20;   animation-duration: 0.01ms !important;

&#x20;   animation-iteration-count: 1 !important;

&#x20;   transition-duration: 0.01ms !important;

&#x20; }



}

#### **Client controller**

api.controller=function($sce) {

&#x20; var c = this;



&#x20; // ── PAGE IDs ──────────────────────────────────────────────

&#x20; var PAGE\_IDS = {

&#x20;   home:           'test\_catalog',

&#x20;   myAppointments: 'my\_appointments'

&#x20; };



&#x20; c.loading         = false;

&#x20; c.searchQuery     = '';

&#x20; c.sortBy          = 'date\_desc';

&#x20; c.filteredReports = \[];

&#x20; c.showModal       = false;

&#x20; c.selectedReport  = null;



&#x20; c.stats = \[

&#x20;   { icon: '📄', label: 'Total Reports',  count: 0 },

&#x20;   { icon: '✅', label: 'Ready',           count: 0 },

&#x20;   { icon: '⏳', label: 'Pending',         count: 0 },

&#x20;   { icon: '🔬', label: 'Tests Completed', count: 0 }

&#x20; ];



&#x20; // ── TRUST HTML FINDINGS ───────────────────────────────────

&#x20; // Converts raw HTML string in findings to trusted HTML so

&#x20; // ng-bind-html renders the formatted table instead of plain text

&#x20; var trustFindings = function(reports) {

&#x20;   reports.forEach(function(r) {

&#x20;     if (r.findings \&\& typeof r.findings === 'string') {

&#x20;       r.findings = $sce.trustAsHtml(r.findings);

&#x20;     }

&#x20;   });

&#x20; };



&#x20; // ── NAVIGATION ────────────────────────────────────────────

&#x20; var \_nav = function(pageId) {

&#x20;   var portalId = window.location.pathname.split('/')\[1] || 'sp';

&#x20;   window.location.href = '/' + portalId + '?id=' + pageId;

&#x20; };



&#x20; // ── INIT ──────────────────────────────────────────────────

&#x20; c.$onInit = function() {

&#x20;   c.buildStats();

&#x20;   c.filterReports();

&#x20; };



&#x20; c.buildStats = function() {

&#x20;   var rpts = c.data.reports || \[];

&#x20;   c.stats\[0].count = rpts.length;

&#x20;   c.stats\[1].count = rpts.filter(function(r) { return r.status === 'ready'; }).length;

&#x20;   c.stats\[2].count = rpts.filter(function(r) { return r.status === 'pending'; }).length;

&#x20;   c.stats\[3].count = rpts.filter(function(r) {

&#x20;     return r.status === 'completed' || r.status === 'ready';

&#x20;   }).length;

&#x20; };



&#x20; c.filterReports = function() {

&#x20;   var all = angular.copy(c.data.reports || \[]);

&#x20;   var q   = (c.searchQuery || '').toLowerCase();



&#x20;   c.filteredReports = all.filter(function(r) {

&#x20;     return !q ||

&#x20;       (r.test\_name     \&\& r.test\_name.toLowerCase().indexOf(q)     !== -1) ||

&#x20;       (r.report\_number \&\& r.report\_number.toLowerCase().indexOf(q) !== -1) ||

&#x20;       (r.doctor\_name   \&\& r.doctor\_name.toLowerCase().indexOf(q)   !== -1);

&#x20;   });



&#x20;   c.filteredReports.sort(function(a, b) {

&#x20;     if (c.sortBy === 'date\_asc')  return (a.report\_date || '').localeCompare(b.report\_date || '');

&#x20;     if (c.sortBy === 'date\_desc') return (b.report\_date || '').localeCompare(a.report\_date || '');

&#x20;     if (c.sortBy === 'name')      return (a.test\_name   || '').localeCompare(b.test\_name   || '');

&#x20;     return 0;

&#x20;   });



&#x20;   // ★ Trust HTML findings for all filtered reports so ng-bind-html renders properly

&#x20;   trustFindings(c.filteredReports);

&#x20; };



&#x20; // ── STATUS HELPERS ────────────────────────────────────────

&#x20; var RPT\_STATUS = {

&#x20;   'ready':      { color: '#10b981', bg: '#dcfce7', label: '✅ Ready'      },

&#x20;   'completed':  { color: '#10b981', bg: '#dcfce7', label: '✅ Completed'  },

&#x20;   'pending':    { color: '#f59e0b', bg: '#fef3c7', label: '⏳ Pending'    },

&#x20;   'processing': { color: '#3b82f6', bg: '#dbeafe', label: '🔬 Processing' }

&#x20; };



&#x20; var \_rptProp = function(s, prop, fallback) {

&#x20;   return (RPT\_STATUS\[s] \&\& RPT\_STATUS\[s]\[prop]) ? RPT\_STATUS\[s]\[prop] : fallback;

&#x20; };



&#x20; c.getStatusColor = function(s) { return \_rptProp(s, 'color', '#94a3b8'); };

&#x20; c.getStatusBg    = function(s) { return \_rptProp(s, 'bg',    '#f1f5f9'); };

&#x20; c.getStatusLabel = function(s) { return \_rptProp(s, 'label', s || 'Ready'); };



&#x20; c.getCategoryIcon = function(cat) {

&#x20;   var icons = {

&#x20;     'blood':      '🩸',

&#x20;     'urine':      '🧪',

&#x20;     'imaging':    '🩻',

&#x20;     'radiology':  '🩻',

&#x20;     'cardiology': '❤️',

&#x20;     'neurology':  '🧠',

&#x20;     'genetics':   '🧬',

&#x20;     'pathology':  '🔬'

&#x20;   };

&#x20;   if (!cat) return '🔬';

&#x20;   var k = cat.toLowerCase();

&#x20;   for (var key in icons) { if (k.indexOf(key) !== -1) return icons\[key]; }

&#x20;   return '🔬';

&#x20; };



&#x20; // ── MODAL ─────────────────────────────────────────────────

&#x20; c.viewDetail = function(report) {

&#x20;   // Use angular.copy so modal has its own independent copy

&#x20;   c.selectedReport = angular.copy(report);



&#x20;   // ★ Trust HTML findings for the modal view

&#x20;   if (c.selectedReport.findings \&\& typeof c.selectedReport.findings === 'string') {

&#x20;     c.selectedReport.findings = $sce.trustAsHtml(c.selectedReport.findings);

&#x20;   }



&#x20;   c.showModal = true;s

&#x20; };



&#x20; c.closeModal = function() {

&#x20;   c.showModal      = false;

&#x20;   c.selectedReport = null;

&#x20; };



&#x20; c.downloadReport = function(report) {

&#x20;   if (report \&\& report.report\_url) {

&#x20;     window.open(report.report\_url, '\_blank');

&#x20;   } else {

&#x20;     alert('Report file is not yet available for download.');

&#x20;   }

&#x20; };



&#x20; // ── NAVIGATION ────────────────────────────────────────────

&#x20; c.goHome     = function() { \_nav(PAGE\_IDS.home); };

&#x20; c.goBookings = function() { \_nav(PAGE\_IDS.myAppointments); };

}

#### **Server script**

(function() {

&#x20; data.reports = \[];



&#x20; try {

&#x20;   var userID    = gs.getUserID();

&#x20;   var userEmail = gs.getUser().getEmail() || '';



&#x20;   // ── STEP 1: Collect ALL patient sys\_ids for this user ─────────────



&#x20;   var patientMap    = {};

&#x20;   var patientSysIds = \[];



&#x20;   // A) By user reference field on patient table

&#x20;   var p1 = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;   p1.addQuery('user', userID);

&#x20;   p1.query();

&#x20;   while (p1.next()) {

&#x20;     var pid1 = p1.getUniqueValue();

&#x20;     if (!patientMap\[pid1]) { patientMap\[pid1] = true; patientSysIds.push(pid1); }

&#x20;   }



&#x20;   // B) By email match

&#x20;   if (userEmail) {

&#x20;     var p2 = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;     p2.addQuery('email', userEmail);

&#x20;     p2.query();

&#x20;     while (p2.next()) {

&#x20;       var pid2 = p2.getUniqueValue();

&#x20;       if (!patientMap\[pid2]) { patientMap\[pid2] = true; patientSysIds.push(pid2); }

&#x20;     }

&#x20;   }



&#x20;   // C) Find patients via appointments created by this user

&#x20;   var a1 = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;   a1.addQuery('created\_by', userID);

&#x20;   a1.query();

&#x20;   while (a1.next()) {

&#x20;     var pRef = a1.getValue('patient');

&#x20;     if (pRef \&\& !patientMap\[pRef]) {

&#x20;       patientMap\[pRef] = true;

&#x20;       patientSysIds.push(pRef);

&#x20;     }

&#x20;   }



&#x20;   if (patientSysIds.length === 0) {

&#x20;     data.reports = \[];

&#x20;     return;

&#x20;   }



&#x20;   // ── STEP 2: Query reports by patient field ────────────────────────



&#x20;   var reportGr = new GlideRecord('x\_1989050\_medica\_0\_report\_table');

&#x20;   reportGr.addQuery('patient', 'IN', patientSysIds.join(','));

&#x20;   reportGr.orderByDesc('sys\_created\_on');

&#x20;   reportGr.query();



&#x20;   while (reportGr.next()) {



&#x20;     // Get appointment details — number, test name, category, test date

&#x20;     var testName        = '';

&#x20;     var testCategory    = '';

&#x20;     var apptNum         = '';

&#x20;     var testDateRaw     = '';

&#x20;     var testDateDisplay = '';

&#x20;     var apptRef         = reportGr.getValue('appointment');



&#x20;     if (apptRef) {

&#x20;       var apptGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;       if (apptGr.get(apptRef)) {

&#x20;         apptNum = apptGr.getValue('appointment\_number') || '';



&#x20;         // Try common date field names on appointment table

&#x20;         var rawApptDate = apptGr.getValue('appointment\_date')

&#x20;                        || apptGr.getValue('scheduled\_date')

&#x20;                        || apptGr.getValue('test\_date')

&#x20;                        || apptGr.getValue('date')

&#x20;                        || '';



&#x20;         if (rawApptDate) {

&#x20;           testDateRaw = rawApptDate;

&#x20;           try {

&#x20;             testDateDisplay = new GlideDateTime(rawApptDate).getLocalDate().getValue();

&#x20;           } catch(de) {

&#x20;             testDateDisplay = rawApptDate.split(' ')\[0] || rawApptDate;

&#x20;           }

&#x20;         }



&#x20;         // Test name and category from linked diagnostic test

&#x20;         var testRef = apptGr.getValue('test');

&#x20;         if (testRef) {

&#x20;           var testGr = new GlideRecord('x\_1989050\_medica\_0\_diagnostic\_test');

&#x20;           if (testGr.get(testRef)) {

&#x20;             testName     = testGr.getValue('test\_name') || '';

&#x20;             testCategory = testGr.getDisplayValue('category') || testGr.getValue('category') || '';

&#x20;           }

&#x20;         }

&#x20;       }

&#x20;     }



&#x20;     // Verified by / doctor name

&#x20;     var doctorName  = '';

&#x20;     var verifiedRef = reportGr.getValue('verified\_by');

&#x20;     if (verifiedRef) {

&#x20;       var docGr = new GlideRecord('sys\_user');

&#x20;       if (docGr.get(verifiedRef)) {

&#x20;         doctorName = docGr.getDisplayValue('name') || '';

&#x20;       }

&#x20;     }



&#x20;     // Format report date

&#x20;     var reportDateRaw     = reportGr.getValue('report\_date') || '';

&#x20;     var reportDateDisplay = '';

&#x20;     if (reportDateRaw) {

&#x20;       try {

&#x20;         reportDateDisplay = new GlideDateTime(reportDateRaw).getLocalDate().getValue();

&#x20;       } catch(de) {

&#x20;         reportDateDisplay = reportDateRaw.split(' ')\[0] || reportDateRaw;

&#x20;       }

&#x20;     }



&#x20;     // Status

&#x20;     var rptStatus = 'ready';

&#x20;     try {

&#x20;       var sv = reportGr.getValue('status');

&#x20;       if (sv) rptStatus = sv;

&#x20;     } catch(se) { /\* field doesn't exist, use default \*/ }



&#x20;     // Findings — preserve full HTML for rich table display

&#x20;     var findingsHTML = '';

&#x20;     try {

&#x20;       findingsHTML = reportGr.getHTMLValue('findings') || '';

&#x20;     } catch(fe) {

&#x20;       findingsHTML = reportGr.getValue('findings') || '';

&#x20;     }



&#x20;     data.reports.push({

&#x20;       sys\_id:              reportGr.getUniqueValue(),

&#x20;       report\_number:       reportGr.getValue('report\_number') || '',

&#x20;       status:              rptStatus,

&#x20;       findings:            findingsHTML,

&#x20;       test\_date:           testDateRaw,

&#x20;       test\_date\_display:   testDateDisplay,

&#x20;       report\_date:         reportDateRaw,

&#x20;       report\_date\_display: reportDateDisplay,

&#x20;       doctor\_name:         doctorName,

&#x20;       report\_url:          '',

&#x20;       test\_name:           testName || ('Report ' + (reportGr.getValue('report\_number') || '')),

&#x20;       test\_category:       testCategory,

&#x20;       appointment\_number:  apptNum

&#x20;     });

&#x20;   }



&#x20; } catch(e) {

&#x20;   gs.error('Lab Reports Widget Error: ' + e.message);

&#x20;   data.error   = e.message;

&#x20;   data.reports = \[];

&#x20; }



})();

