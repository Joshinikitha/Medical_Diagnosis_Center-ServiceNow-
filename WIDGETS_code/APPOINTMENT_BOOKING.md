# **APPOINTMENT\_BOOKING**

#### **HTML**

<div class="appt-booking">

&#x20; <!-- PROGRESS STEPS -->

&#x20; <div class="progress-wrap">

&#x20;   <div class="progress-step" ng-class="{'active': c.step >= 1, 'done': c.step > 1}">

&#x20;     <div class="step-circle"><i class="fa fa-check" ng-if="c.step > 1"></i><span ng-if="c.step <= 1">1</span></div>

&#x20;     <span class="step-label">Details</span>

&#x20;   </div>

&#x20;   <div class="step-line" ng-class="{'filled': c.step > 1}"></div>

&#x20;   <div class="progress-step" ng-class="{'active': c.step >= 2, 'done': c.step > 2}">

&#x20;     <div class="step-circle"><i class="fa fa-check" ng-if="c.step > 2"></i><span ng-if="c.step <= 2">2</span></div>

&#x20;     <span class="step-label">Schedule</span>

&#x20;   </div>

&#x20;   <div class="step-line" ng-class="{'filled': c.step > 2}"></div>

&#x20;   <div class="progress-step" ng-class="{'active': c.step >= 3, 'done': c.step > 3}">

&#x20;     <div class="step-circle"><i class="fa fa-check" ng-if="c.step > 3"></i><span ng-if="c.step <= 3">3</span></div>

&#x20;     <span class="step-label">Payment</span>

&#x20;   </div>

&#x20;   <div class="step-line" ng-class="{'filled': c.step > 3}"></div>

&#x20;   <div class="progress-step" ng-class="{'active': c.step >= 4}">

&#x20;     <div class="step-circle"><span>4</span></div>

&#x20;     <span class="step-label">Done</span>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- TEST BANNER — ng-bind used instead of {{}} for price -->

&#x20; <div class="test-banner" ng-if="c.selectedTest">

&#x20;   <div class="test-banner-icon" ng-bind="c.getCategoryIcon(c.selectedTest.category)"></div>

&#x20;   <div class="test-banner-info">

&#x20;     <span class="test-banner-name" ng-bind="c.selectedTest.test\_name"></span>

&#x20;     <span class="test-banner-meta">

&#x20;       <span ng-bind="c.selectedTest.category"></span> \&middot;

&#x20;       Code: <span ng-bind="c.selectedTest.test\_code"></span> \&middot;

&#x20;       Duration: <span ng-bind="c.selectedTest.test\_duration"></span>

&#x20;     </span>

&#x20;   </div>

&#x20;   <div class="test-banner-price">

&#x20;     <span class="price-tag">$<span ng-bind="c.testPrice"></span></span>

&#x20;     <button class="btn-change-test" ng-click="c.changeTest()">Change Test</button>

&#x20;   </div>

&#x20; </div>



&#x20; <div class="no-test-warn" ng-if="!c.selectedTest">

&#x20;   <i class="fa fa-exclamation-triangle"></i>

&#x20;   No test selected. <a ng-click="c.changeTest()">Back to catalog</a>

&#x20; </div>



&#x20; <!-- ===== STEP 1: PATIENT DETAILS ===== -->

&#x20; <div class="booking-step" ng-show="c.step === 1">

&#x20;   <div class="step-header">

&#x20;     <h2>\&#128100; Patient Information</h2>

&#x20;     <p>Fill in your personal details to proceed.</p>

&#x20;   </div>



&#x20;   <div class="form-card">

&#x20;     <div class="form-grid">



&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.first\_name}">

&#x20;         <label class="form-label req">First Name</label>

&#x20;         <input class="form-input" type="text" placeholder="First name"

&#x20;           ng-model="c.form.first\_name" ng-change="c.clearError('first\_name')" />

&#x20;         <span class="err-msg" ng-if="c.errors.first\_name" ng-bind="c.errors.first\_name"></span>

&#x20;       </div>



&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.last\_name}">

&#x20;         <label class="form-label req">Last Name</label>

&#x20;         <input class="form-input" type="text" placeholder="Last name"

&#x20;           ng-model="c.form.last\_name" ng-change="c.clearError('last\_name')" />

&#x20;         <span class="err-msg" ng-if="c.errors.last\_name" ng-bind="c.errors.last\_name"></span>

&#x20;       </div>



&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.email}">

&#x20;         <label class="form-label req">Email Address</label>

&#x20;         <input class="form-input" type="email" placeholder="you@example.com"

&#x20;           ng-model="c.form.email" ng-change="c.clearError('email')" />

&#x20;         <span class="err-msg" ng-if="c.errors.email" ng-bind="c.errors.email"></span>

&#x20;       </div>



&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.phone\_number}">

&#x20;         <label class="form-label req">Phone Number</label>

&#x20;         <input class="form-input" type="tel" placeholder="+1 555 000 0000"

&#x20;           ng-model="c.form.phone\_number" ng-change="c.clearError('phone\_number')" />

&#x20;         <span class="err-msg" ng-if="c.errors.phone\_number" ng-bind="c.errors.phone\_number"></span>

&#x20;       </div>



&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.date\_of\_birth}">

&#x20;         <label class="form-label req">Date of Birth</label>

&#x20;         <input class="form-input" type="date"

&#x20;           ng-model="c.form.date\_of\_birth" ng-change="c.clearError('date\_of\_birth')" />

&#x20;         <span class="err-msg" ng-if="c.errors.date\_of\_birth" ng-bind="c.errors.date\_of\_birth"></span>

&#x20;       </div>



&#x20;       <!-- GENDER custom dropdown -->

&#x20;       <div class="form-group" ng-class="{'has-error': c.errors.gender}">

&#x20;         <label class="form-label req">Gender</label>

&#x20;         <div class="cust-select" ng-class="{'open': c.genderOpen}">

&#x20;           <div class="cust-sel-trigger" ng-click="c.genderOpen = !c.genderOpen; c.bankOpen = false;">

&#x20;             <span class="cust-sel-val" ng-if="!c.form.gender" style="color:#94a3b8;">-- Select Gender --</span>

&#x20;             <span class="cust-sel-val" ng-if="c.form.gender" ng-bind="c.getGenderLabel(c.form.gender)"></span>

&#x20;             <i class="fa" ng-class="c.genderOpen ? 'fa-chevron-up' : 'fa-chevron-down'" style="color:#94a3b8;font-size:12px;"></i>

&#x20;           </div>

&#x20;           <div class="cust-sel-menu" ng-if="c.genderOpen">

&#x20;             <div class="cust-sel-item" ng-repeat="opt in c.genderOptions"

&#x20;               ng-click="c.selectGender(opt.value)"

&#x20;               ng-class="{'selected': c.form.gender === opt.value}"

&#x20;               ng-bind="opt.label">

&#x20;             </div>

&#x20;           </div>

&#x20;         </div>

&#x20;         <span class="err-msg" ng-if="c.errors.gender" ng-bind="c.errors.gender"></span>

&#x20;       </div>



&#x20;       <div class="form-group form-full">

&#x20;         <label class="form-label">Address</label>

&#x20;         <textarea class="form-input" rows="2" placeholder="Your full address"

&#x20;           ng-model="c.form.address"></textarea>

&#x20;       </div>



&#x20;     </div>

&#x20;   </div>



&#x20;   <div class="step-actions">

&#x20;     <button class="btn-back" ng-click="c.changeTest()"><i class="fa fa-arrow-left"></i> Back to Catalog</button>

&#x20;     <button class="btn-next" ng-click="c.validateStep1()">Continue <i class="fa fa-arrow-right"></i></button>

&#x20;   </div>

&#x20; </div>

&#x20; <!-- Validation message -->

<div ng-if="c.validationMsg" style="background:#fef2f2;border:2px solid #fca5a5;border-radius:10px;padding:12px 16px;margin-bottom:16px;color:#b91c1c;font-size:13px;font-weight:600;display:flex;align-items:center;gap:8px;">

&#x20; <i class="fa fa-exclamation-circle"></i>

&#x20; <span>{{c.validationMsg}}</span>

</div>



&#x20; <!-- ===== STEP 2: SCHEDULE ===== -->

&#x20; <div class="booking-step" ng-show="c.step === 2">

&#x20;   <div class="step-header">

&#x20;     <h2>\&#128197; Schedule Appointment</h2>

&#x20;     <p>Choose your preferred date and time slot.</p>

&#x20;   </div>



&#x20;   <div class="form-card">

&#x20;     <div class="form-group" ng-class="{'has-error': c.errors.scheduled\_date}">

&#x20;       <label class="form-label req">Preferred Date</label>

&#x20;       <input class="form-input" type="date" ng-model="c.form.scheduled\_date"

&#x20;         ng-attr-min="{{c.minDate}}" ng-change="c.onDateChange()" />

&#x20;       <span class="err-msg" ng-if="c.errors.scheduled\_date" ng-bind="c.errors.scheduled\_date"></span>

&#x20;     </div>



&#x20;     <div class="slots-section" ng-if="c.form.scheduled\_date">

&#x20;       <label class="form-label req" style="display:block;margin-bottom:10px;">Available Time Slots</label>

&#x20;       <div class="slots-grid">

&#x20;         <button class="slot-btn" ng-repeat="slot in c.timeSlots"

&#x20;           ng-class="{'selected': c.form.slot\_time === slot}"

&#x20;           ng-click="c.selectSlot(slot)"

&#x20;           ng-bind="slot">

&#x20;         </button>

&#x20;       </div>

&#x20;       <span class="err-msg" ng-if="c.errors.slot\_time" ng-bind="c.errors.slot\_time"></span>

&#x20;     </div>



&#x20;     <div class="form-group" style="margin-top:20px;">

&#x20;       <label class="form-label">Notes (optional)</label>

&#x20;       <textarea class="form-input" rows="3" placeholder="Any special instructions..."

&#x20;         ng-model="c.form.notes"></textarea>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Booking Summary — FIX: use ng-bind for all dynamic values -->

&#x20;   <div class="booking-summary">

&#x20;     <h4>\&#128203; Booking Summary</h4>

&#x20;     <div class="sum-row">

&#x20;       <span>Test</span>

&#x20;       <strong ng-bind="c.selectedTest.test\_name"></strong>

&#x20;     </div>

&#x20;     <div class="sum-row">

&#x20;       <span>Patient</span>

&#x20;       <strong><span ng-bind="c.form.first\_name"></span> <span ng-bind="c.form.last\_name"></span></strong>

&#x20;     </div>

&#x20;     <div class="sum-row" ng-if="c.form.scheduled\_date">

&#x20;       <span>Date</span>

&#x20;       <strong ng-bind="c.formatDateDisplay(c.form.scheduled\_date)"></strong>

&#x20;     </div>

&#x20;     <div class="sum-row" ng-if="c.form.slot\_time">

&#x20;       <span>Time</span>

&#x20;       <strong ng-bind="c.form.slot\_time"></strong>

&#x20;     </div>

&#x20;     <div class="sum-row">

&#x20;       <span>Amount</span>

&#x20;       <strong style="color:#0a2463;">$<span ng-bind="c.testPrice"></span></strong>

&#x20;     </div>

&#x20;   </div>



&#x20;   <div class="step-actions">

&#x20;     <button class="btn-back" ng-click="c.prevStep()"><i class="fa fa-arrow-left"></i> Back</button>

&#x20;     <button class="btn-next" ng-click="c.validateStep2()">Continue to Payment <i class="fa fa-arrow-right"></i></button>

&#x20;   </div>

&#x20; </div>

&#x20; <!-- Validation message -->

<div ng-if="c.validationMsg" style="background:#fef2f2;border:2px solid #fca5a5;border-radius:10px;padding:12px 16px;margin-bottom:16px;color:#b91c1c;font-size:13px;font-weight:600;display:flex;align-items:center;gap:8px;">

&#x20; <i class="fa fa-exclamation-circle"></i>

&#x20; <span>{{c.validationMsg}}</span>

</div>



&#x20; <!-- ===== STEP 3: PAYMENT ===== -->

&#x20; <div class="booking-step" ng-show="c.step === 3">

&#x20;   <div class="step-header">

&#x20;     <h2>\&#128179; Payment</h2>

&#x20;     <p>Select a payment method and confirm your booking.</p>

&#x20;   </div>



&#x20;   <!-- Order Summary — all using ng-bind -->

&#x20;   <div class="order-card">

&#x20;     <div class="order-hdr">Order Summary</div>

&#x20;     <div class="order-row">

&#x20;       <span ng-bind="c.selectedTest.test\_name"></span>

&#x20;       <span>$<span ng-bind="c.testPrice"></span></span>

&#x20;     </div>

&#x20;     <div class="order-row">

&#x20;       <span>Date \&amp; Time</span>

&#x20;       <span><span ng-bind="c.formatDateDisplay(c.form.scheduled\_date)"></span> \&middot; <span ng-bind="c.form.slot\_time"></span></span>

&#x20;     </div>

&#x20;     <div class="order-row"><span>Service Fee</span><span>$0.00</span></div>

&#x20;     <div class="order-divider"></div>

&#x20;     <div class="order-total">

&#x20;       <span>Total</span>

&#x20;       <span class="order-total-price">$<span ng-bind="c.testPrice"></span></span>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Payment methods -->

&#x20;   <label class="form-label" style="display:block;margin-bottom:12px;">Select Payment Method</label>

&#x20;   <div class="pay-methods">

&#x20;     <div class="pay-method" ng-class="{'active': c.payment.method === 'card'}" ng-click="c.setPaymentMethod('card')">

&#x20;       <span class="pay-icon">\&#128179;</span><span class="pay-lbl">Card</span>

&#x20;       <span class="pay-tick" ng-if="c.payment.method === 'card'">\&#10003;</span>

&#x20;     </div>

&#x20;     <div class="pay-method" ng-class="{'active': c.payment.method === 'upi'}" ng-click="c.setPaymentMethod('upi')">

&#x20;       <span class="pay-icon">\&#128241;</span><span class="pay-lbl">UPI</span>

&#x20;       <span class="pay-tick" ng-if="c.payment.method === 'upi'">\&#10003;</span>

&#x20;     </div>

&#x20;     <div class="pay-method" ng-class="{'active': c.payment.method === 'netbanking'}" ng-click="c.setPaymentMethod('netbanking')">

&#x20;       <span class="pay-icon">\&#127974;</span><span class="pay-lbl">Net Banking</span>

&#x20;       <span class="pay-tick" ng-if="c.payment.method === 'netbanking'">\&#10003;</span>

&#x20;     </div>

&#x20;     <div class="pay-method" ng-class="{'active': c.payment.method === 'insurance'}" ng-click="c.setPaymentMethod('insurance')">

&#x20;       <span class="pay-icon">\&#127973;</span><span class="pay-lbl">Insurance</span>

&#x20;       <span class="pay-tick" ng-if="c.payment.method === 'insurance'">\&#10003;</span>

&#x20;     </div>

&#x20;     <div class="pay-method" ng-class="{'active': c.payment.method === 'cash'}" ng-click="c.setPaymentMethod('cash')">

&#x20;       <span class="pay-icon">\&#128181;</span><span class="pay-lbl">Pay on Arrival</span>

&#x20;       <span class="pay-tick" ng-if="c.payment.method === 'cash'">\&#10003;</span>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Card -->

&#x20;   <div class="form-card" ng-if="c.payment.method === 'card'">

&#x20;     <div class="secure-tag"><i class="fa fa-lock"></i> Secure Demo Payment</div>

&#x20;     <div class="form-grid">

&#x20;       <div class="form-group form-full">

&#x20;         <label class="form-label">Cardholder Name</label>

&#x20;         <input class="form-input" type="text" placeholder="Name on card" ng-model="c.payment.card\_name" />

&#x20;       </div>

&#x20;       <div class="form-group form-full">

&#x20;         <label class="form-label">Card Number</label>

&#x20;         <input class="form-input" type="text" placeholder="4242 4242 4242 4242" maxlength="19" ng-model="c.payment.card\_number" />

&#x20;       </div>

&#x20;       <div class="form-group">

&#x20;         <label class="form-label">Expiry</label>

&#x20;         <input class="form-input" type="text" placeholder="MM/YY" maxlength="5" ng-model="c.payment.expiry" />

&#x20;       </div>

&#x20;       <div class="form-group">

&#x20;         <label class="form-label">CVV</label>

&#x20;         <input class="form-input" type="password" placeholder="\*\*\*" maxlength="4" ng-model="c.payment.cvv" />

&#x20;       </div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- UPI -->

&#x20;   <div class="form-card" ng-if="c.payment.method === 'upi'">

&#x20;     <div class="secure-tag"><i class="fa fa-lock"></i> UPI Demo Payment</div>

&#x20;     <div class="form-group" style="margin-bottom:16px;">

&#x20;       <label class="form-label">UPI ID</label>

&#x20;       <input class="form-input" type="text" placeholder="yourname@upi" ng-model="c.payment.upi\_id" />

&#x20;     </div>

&#x20;     <label class="form-label" style="display:block;margin-bottom:10px;">Or choose app</label>

&#x20;     <div class="upi-apps">

&#x20;       <div class="upi-app-tile" ng-class="{'upi-active': c.payment.upi\_app === 'gpay'}" ng-click="c.selectUpiApp('gpay')">

&#x20;         <div class="upi-app-logo" style="background:linear-gradient(135deg,#4285f4,#34a853);">G</div>

&#x20;         <span>GPay</span>

&#x20;       </div>

&#x20;       <div class="upi-app-tile" ng-class="{'upi-active': c.payment.upi\_app === 'phonepe'}" ng-click="c.selectUpiApp('phonepe')">

&#x20;         <div class="upi-app-logo" style="background:#5f259f;">P</div>

&#x20;         <span>PhonePe</span>

&#x20;       </div>

&#x20;       <div class="upi-app-tile" ng-class="{'upi-active': c.payment.upi\_app === 'paytm'}" ng-click="c.selectUpiApp('paytm')">

&#x20;         <div class="upi-app-logo" style="background:#00b9f5;color:#002970;">P</div>

&#x20;         <span>Paytm</span>

&#x20;       </div>

&#x20;       <div class="upi-app-tile" ng-class="{'upi-active': c.payment.upi\_app === 'bhim'}" ng-click="c.selectUpiApp('bhim')">

&#x20;         <div class="upi-app-logo" style="background:#ff6600;">B</div>

&#x20;         <span>BHIM</span>

&#x20;       </div>

&#x20;       <div class="upi-app-tile" ng-class="{'upi-active': c.payment.upi\_app === 'amazonpay'}" ng-click="c.selectUpiApp('amazonpay')">

&#x20;         <div class="upi-app-logo" style="background:#ff9900;color:#232f3e;">A</div>

&#x20;         <span>Amazon</span>

&#x20;       </div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Net Banking -->

&#x20;   <div class="form-card" ng-if="c.payment.method === 'netbanking'">

&#x20;     <div class="secure-tag"><i class="fa fa-lock"></i> Net Banking Demo</div>

&#x20;     <div class="form-group">

&#x20;       <label class="form-label">Select Your Bank</label>

&#x20;       <div class="cust-select" ng-class="{'open': c.bankOpen}">

&#x20;         <div class="cust-sel-trigger" ng-click="c.bankOpen = !c.bankOpen; c.genderOpen = false;">

&#x20;           <span class="cust-sel-val" ng-if="!c.payment.bank" style="color:#94a3b8;">-- Select Bank --</span>

&#x20;           <span class="cust-sel-val" ng-if="c.payment.bank" ng-bind="c.getBankLabel(c.payment.bank)"></span>

&#x20;           <i class="fa" ng-class="c.bankOpen ? 'fa-chevron-up' : 'fa-chevron-down'" style="color:#94a3b8;font-size:12px;"></i>

&#x20;         </div>

&#x20;         <div class="cust-sel-menu" ng-if="c.bankOpen">

&#x20;           <div class="cust-sel-item" ng-repeat="b in c.bankOptions"

&#x20;             ng-click="c.selectBank(b.value)"

&#x20;             ng-class="{'selected': c.payment.bank === b.value}"

&#x20;             ng-bind="b.label">

&#x20;           </div>

&#x20;         </div>

&#x20;       </div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Insurance -->

&#x20;   <div class="form-card" ng-if="c.payment.method === 'insurance'">

&#x20;     <div class="secure-tag">\&#127973; Insurance Payment</div>

&#x20;     <div class="form-grid">

&#x20;       <div class="form-group">

&#x20;         <label class="form-label">Provider</label>

&#x20;         <input class="form-input" type="text" placeholder="e.g. BlueCross, Aetna" ng-model="c.payment.insurance\_provider" />

&#x20;       </div>

&#x20;       <div class="form-group">

&#x20;         <label class="form-label">Policy Number</label>

&#x20;         <input class="form-input" type="text" placeholder="Policy / Member ID" ng-model="c.payment.policy\_number" />

&#x20;       </div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- Cash -->

&#x20;   <div class="form-card cash-card" ng-if="c.payment.method === 'cash'">

&#x20;     <div class="cash-emoji">\&#128181;</div>

&#x20;     <h4>Pay on Arrival</h4>

&#x20;     <p>Pay <strong>$<span ng-bind="c.testPrice"></span></strong> at the center when you arrive.</p>

&#x20;     <p class="cash-note">Carry a valid ID. Please arrive 15 minutes early.</p>

&#x20;   </div>



&#x20;   <div class="step-actions">

&#x20;     <button class="btn-back" ng-click="c.prevStep()"><i class="fa fa-arrow-left"></i> Back</button>

&#x20;     <button class="btn-pay" ng-click="c.processPayment()" ng-disabled="c.processing">

&#x20;       <span ng-if="!c.processing">

&#x20;         <i class="fa fa-lock"></i> Confirm \&amp; Pay $<span ng-bind="c.testPrice"></span>

&#x20;       </span>

&#x20;       <span ng-if="c.processing"><i class="fa fa-spinner fa-spin"></i> Processing...</span>

&#x20;     </button>

&#x20;   </div>

&#x20; </div>



&#x20; <!-- ===== STEP 4: SUCCESS ===== -->

&#x20; <div class="booking-step success-wrap" ng-show="c.step === 4">

&#x20;   <div class="success-circle"><i class="fa fa-check"></i></div>

&#x20;   <h2 class="success-title">Appointment Confirmed! \&#127881;</h2>

&#x20;   <p class="success-sub">Pending admin approval. Confirmation sent to <strong ng-bind="c.form.email"></strong></p>



&#x20;   <div class="conf-card">

&#x20;     <div class="conf-row"><span>Appointment #</span><strong class="appt-code" ng-bind="c.data.appointmentNumber"></strong></div>

&#x20;     <div class="conf-row"><span>Patient</span><strong><span ng-bind="c.form.first\_name"></span> <span ng-bind="c.form.last\_name"></span></strong></div>

&#x20;     <div class="conf-row"><span>Test</span><strong ng-bind="c.selectedTest.test\_name"></strong></div>

&#x20;     <div class="conf-row"><span>Date \&amp; Time</span><strong><span ng-bind="c.formatDateDisplay(c.form.scheduled\_date)"></span> \&middot; <span ng-bind="c.form.slot\_time"></span></strong></div>

&#x20;     <div class="conf-row"><span>Amount Paid</span><strong class="paid-green">$<span ng-bind="c.testPrice"></span> \&#10003;</strong></div>

&#x20;     <div class="conf-row"><span>Payment Via</span><strong ng-bind="c.getPaymentLabel(c.payment.method)"></strong></div>

&#x20;     <div class="conf-row"><span>Status</span><strong class="status-warn">\&#9203; Pending Approval</strong></div>

&#x20;   </div>



&#x20;   <div class="next-steps-wrap">

&#x20;     <h4>What happens next?</h4>

&#x20;     <div class="next-step-row"><span class="ns-ico">\&#128231;</span><div><strong>Confirmation Email</strong><span>Check your inbox for booking details</span></div></div>

&#x20;     <div class="next-step-row"><span class="ns-ico">\&#9989;</span><div><strong>Admin Approval</strong><span>Reviewed within 24 hours</span></div></div>

&#x20;     <div class="next-step-row"><span class="ns-ico">\&#128276;</span><div><strong>Reminder</strong><span>You will get an alert 24h before your test</span></div></div>

&#x20;   </div>



&#x20;   <div class="success-btns">

&#x20;     <button class="btn-next" ng-click="c.viewMyAppointments()"><i class="fa fa-list"></i> View My Bookings</button>

&#x20;     <button class="btn-back" ng-click="c.bookAnother()">Book Another Test</button>

&#x20;   </div>

&#x20; </div>



</div>



#### **CSS**



.appt-booking {

&#x20; --blue:#0a2463; --blue2:#1e3a8a; --cyan:#00b4d8; --cyan2:#0096c7;

&#x20; --green:#10b981; --amber:#f59e0b; --red:#ef4444;

&#x20; --g50:#f8fafc; --g100:#f1f5f9; --g200:#e2e8f0;

&#x20; --g400:#94a3b8; --g600:#475569; --g800:#1e293b; --wht:#ffffff;

&#x20; --r:14px; --sh:0 1px 4px rgba(0,0,0,.07);

&#x20; font-family:'Segoe UI',system-ui,sans-serif;

&#x20; max-width:800px; margin:0 auto;

&#x20; padding:28px 20px 60px; background:var(--g50); min-height:100vh;

}



/\* ── PROGRESS ──────────────────────────────────────── \*/

.progress-wrap { display:flex; align-items:center; justify-content:center; margin-bottom:32px; gap:0; }

.progress-step { display:flex; flex-direction:column; align-items:center; gap:6px; }

.step-circle {

&#x20; width:42px; height:42px; border-radius:50%; border:3px solid var(--g200);

&#x20; background:var(--g200); color:var(--g400);

&#x20; display:flex; align-items:center; justify-content:center;

&#x20; font-size:15px; font-weight:700; transition:all .3s;

}

.progress-step.active .step-circle { background:var(--blue); border-color:var(--blue); color:#fff; box-shadow:0 4px 12px rgba(10,36,99,.25); }

.progress-step.done   .step-circle { background:var(--green); border-color:var(--green); color:#fff; }

.step-label { font-size:11px; font-weight:600; color:var(--g400); white-space:nowrap; }

.progress-step.active .step-label,

.progress-step.done   .step-label { color:var(--blue); }

.step-line { flex:1; min-width:40px; max-width:90px; height:3px; background:var(--g200); margin-top:-22px; transition:background .3s; }

.step-line.filled { background:var(--green); }



/\* ── TEST BANNER ───────────────────────────────────── \*/

.test-banner {

&#x20; display:flex; align-items:center; gap:14px; flex-wrap:wrap;

&#x20; background:linear-gradient(135deg,#eff6ff,#dbeafe);

&#x20; border:1px solid #bfdbfe; border-radius:var(--r);

&#x20; padding:14px 18px; margin-bottom:24px;

}

.test-banner-icon { font-size:34px; flex-shrink:0; }

.test-banner-info { flex:1; }

.test-banner-name { display:block; font-size:16px; font-weight:700; color:var(--blue); }

.test-banner-meta { display:block; font-size:12px; color:var(--g600); margin-top:2px; }

.test-banner-price { display:flex; flex-direction:column; align-items:flex-end; gap:6px; }

.price-tag { font-size:26px; font-weight:800; color:var(--blue); }

.btn-change-test {

&#x20; background:none; border:1px solid var(--cyan); color:var(--cyan2);

&#x20; padding:4px 12px; border-radius:20px; font-size:12px; font-weight:600; cursor:pointer;

}

.btn-change-test:hover { background:var(--cyan); color:#fff; }

.no-test-warn {

&#x20; background:#fef3c7; border:1px solid #fcd34d; border-radius:10px;

&#x20; padding:12px 16px; color:#92400e; font-size:14px; margin-bottom:20px;

}

.no-test-warn a { color:var(--cyan2); cursor:pointer; text-decoration:underline; }



/\* ── STEP HEADER ───────────────────────────────────── \*/

.step-header { margin-bottom:20px; }

.step-header h2 { font-size:21px; font-weight:800; color:var(--g800); margin:0 0 4px; }

.step-header p  { color:var(--g600); font-size:13px; margin:0; }



/\* ── FORM CARD ─────────────────────────────────────── \*/

.form-card {

&#x20; background:var(--wht); border-radius:var(--r); border:1px solid var(--g200);

&#x20; padding:24px; box-shadow:var(--sh); margin-bottom:20px;

}

.form-grid { display:grid; grid-template-columns:1fr 1fr; gap:16px; }

.form-group { display:flex; flex-direction:column; gap:5px; }

.form-full { grid-column:1 / -1; }

.form-label { font-size:11px; font-weight:700; color:var(--g800); text-transform:uppercase; letter-spacing:.4px; }

.form-label.req::after { content:' \*'; color:var(--red); }



/\* ── INPUTS ────────────────────────────────────────── \*/

.form-input {

&#x20; padding:11px 14px; border:2px solid var(--g200); border-radius:10px;

&#x20; font-size:14px; color:var(--g800); background:var(--wht);

&#x20; outline:none; transition:border .2s; width:100%; box-sizing:border-box;

&#x20; font-family:inherit;

}

.form-input:focus { border-color:var(--cyan); }

.has-error .form-input { border-color:var(--red); }

textarea.form-input { resize:vertical; min-height:72px; }

.err-msg { font-size:12px; color:var(--red); font-weight:500; }



/\* ── CUSTOM SELECT (fixes broken <select> in Service Portal) ── \*/

.cust-select { position:relative; }

.cust-sel-trigger {

&#x20; display:flex; align-items:center; justify-content:space-between;

&#x20; padding:11px 14px; border:2px solid var(--g200); border-radius:10px;

&#x20; background:var(--wht); cursor:pointer; transition:border .2s;

&#x20; font-size:14px; color:var(--g800); user-select:none;

}

.cust-sel-trigger:hover,

.cust-select.open .cust-sel-trigger { border-color:var(--cyan); }

.cust-sel-val { flex:1; }

.cust-sel-menu {

&#x20; position:absolute; top:calc(100% + 4px); left:0; right:0; z-index:999;

&#x20; background:var(--wht); border:2px solid var(--cyan); border-radius:10px;

&#x20; box-shadow:0 8px 24px rgba(0,0,0,.12); overflow:hidden;

}

.cust-sel-item {

&#x20; padding:11px 16px; font-size:14px; color:var(--g800);

&#x20; cursor:pointer; transition:background .12s; border-bottom:1px solid var(--g100);

}

.cust-sel-item:last-child { border-bottom:none; }

.cust-sel-item:hover  { background:#f0f9ff; }

.cust-sel-item.selected { background:#dbeafe; color:var(--blue); font-weight:600; }

.has-error .cust-sel-trigger { border-color:var(--red); }



/\* ── TIME SLOTS ────────────────────────────────────── \*/

.slots-section { margin-top:16px; }

.slots-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(88px,1fr)); gap:7px; margin-top:8px; }

.slot-btn {

&#x20; padding:8px 4px; border:2px solid var(--g200); border-radius:8px;

&#x20; background:var(--wht); color:var(--g800); font-size:12px; font-weight:600;

&#x20; cursor:pointer; transition:all .15s; text-align:center;

}

.slot-btn:hover   { border-color:var(--cyan); color:var(--cyan2); background:#f0f9ff; }

.slot-btn.selected { background:var(--blue); border-color:var(--blue); color:#fff; }



/\* ── BOOKING SUMMARY ───────────────────────────────── \*/

.booking-summary {

&#x20; background:#f0fdf4; border:1px solid #bbf7d0; border-radius:var(--r);

&#x20; padding:16px 20px; margin-bottom:20px;

}

.booking-summary h4 { font-size:13px; font-weight:700; color:#166534; margin:0 0 10px; }

.sum-row { display:flex; justify-content:space-between; font-size:13px; padding:5px 0; border-bottom:1px solid #dcfce7; }

.sum-row:last-child { border-bottom:none; }

.sum-row span   { color:var(--g600); }

.sum-row strong { color:var(--g800); }



/\* ── ORDER CARD ────────────────────────────────────── \*/

.order-card { background:var(--wht); border-radius:var(--r); border:1px solid var(--g200); overflow:hidden; margin-bottom:20px; }

.order-hdr  { background:var(--blue); color:#fff; padding:13px 18px; font-weight:700; font-size:14px; }

.order-row  { display:flex; justify-content:space-between; padding:11px 18px; border-bottom:1px solid var(--g100); font-size:13px; color:var(--g800); }

.order-divider { border-top:2px solid var(--g200); }

.order-total { display:flex; justify-content:space-between; padding:14px 18px; font-size:15px; font-weight:700; color:var(--g800); }

.order-total-price { font-size:22px; color:var(--blue); }



/\* ── PAYMENT METHODS ───────────────────────────────── \*/

.pay-methods { display:grid; grid-template-columns:repeat(5,1fr); gap:10px; margin-bottom:20px; }

.pay-method {

&#x20; display:flex; flex-direction:column; align-items:center; gap:6px;

&#x20; padding:14px 8px; border:2px solid var(--g200); border-radius:12px;

&#x20; background:var(--wht); cursor:pointer; transition:all .2s;

&#x20; position:relative; text-align:center;

}

.pay-method:hover    { border-color:var(--cyan); }

.pay-method.active   { border-color:var(--blue); background:#eff6ff; box-shadow:0 4px 12px rgba(10,36,99,.1); }

.pay-icon  { font-size:24px; }

.pay-lbl   { font-size:11px; font-weight:700; color:var(--g800); line-height:1.2; }

.pay-tick  {

&#x20; position:absolute; top:5px; right:7px; width:17px; height:17px;

&#x20; background:var(--green); color:#fff; border-radius:50%;

&#x20; display:flex; align-items:center; justify-content:center; font-size:10px; font-weight:700;

}



/\* ── SECURE TAG ────────────────────────────────────── \*/

.secure-tag {

&#x20; display:flex; align-items:center; gap:8px;

&#x20; background:#ecfdf5; border:1px solid #a7f3d0; border-radius:8px;

&#x20; padding:9px 14px; color:#065f46; font-size:13px; font-weight:600; margin-bottom:18px;

}



/\* ── UPI APPS ──────────────────────────────────────── \*/

.upi-apps { display:flex; gap:10px; flex-wrap:wrap; }

.upi-app-tile {

&#x20; display:flex; flex-direction:column; align-items:center; gap:6px;

&#x20; padding:12px 14px; border:2px solid var(--g200); border-radius:12px;

&#x20; background:var(--wht); cursor:pointer; transition:all .2s;

&#x20; min-width:64px; font-size:11px; font-weight:700; color:var(--g800);

}

.upi-app-tile:hover  { border-color:var(--cyan); }

.upi-app-tile.upi-active { border-color:var(--blue); background:#eff6ff; color:var(--blue); }

.upi-app-logo {

&#x20; width:36px; height:36px; border-radius:10px;

&#x20; display:flex; align-items:center; justify-content:center;

&#x20; font-size:16px; font-weight:900; color:#fff;

}



/\* ── CASH ──────────────────────────────────────────── \*/

.cash-card { text-align:center; padding:28px !important; }

.cash-emoji { font-size:44px; margin-bottom:10px; }

.cash-card h4 { font-size:17px; color:var(--g800); margin:0 0 8px; }

.cash-card p  { color:var(--g600); font-size:14px; margin:0 0 6px; }

.cash-note    { color:var(--g400); font-size:12px; font-style:italic; }



/\* ── STEP ACTIONS ──────────────────────────────────── \*/

.step-actions { display:flex; justify-content:space-between; align-items:center; gap:12px; flex-wrap:wrap; margin-top:4px; }

.btn-back, .btn-next, .btn-pay {

&#x20; display:inline-flex; align-items:center; gap:7px;

&#x20; padding:12px 24px; border-radius:10px; font-size:14px; font-weight:700;

&#x20; cursor:pointer; border:none; transition:all .2s;

}

.btn-back { background:var(--wht); color:var(--g600); border:2px solid var(--g200); }

.btn-back:hover { border-color:var(--g400); }

.btn-next { background:linear-gradient(135deg,var(--blue),var(--blue2)); color:#fff; box-shadow:0 4px 12px rgba(10,36,99,.28); }

.btn-next:hover { transform:translateY(-1px); box-shadow:0 6px 18px rgba(10,36,99,.34); }

.btn-pay  { background:linear-gradient(135deg,var(--green),#059669); color:#fff; box-shadow:0 4px 12px rgba(16,185,129,.3); padding:13px 28px; font-size:15px; }

.btn-pay:hover    { transform:translateY(-1px); }

.btn-pay:disabled { opacity:.65; cursor:not-allowed; transform:none; }



/\* ── SUCCESS ───────────────────────────────────────── \*/

.success-wrap   { text-align:center; padding-top:16px; }

.success-circle {

&#x20; width:88px; height:88px; background:var(--green); border-radius:50%;

&#x20; display:inline-flex; align-items:center; justify-content:center;

&#x20; font-size:38px; color:#fff; margin-bottom:20px;

&#x20; box-shadow:0 8px 28px rgba(16,185,129,.38);

&#x20; animation:pop .5s cubic-bezier(.36,.07,.19,.97);

}

@keyframes pop { 0%{transform:scale(0)} 80%{transform:scale(1.1)} 100%{transform:scale(1)} }

.success-title { font-size:26px; font-weight:800; color:var(--g800); margin:0 0 10px; }

.success-sub   { color:var(--g600); font-size:14px; margin:0 0 24px; }

.conf-card {

&#x20; background:var(--wht); border-radius:var(--r); border:1px solid var(--g200);

&#x20; padding:20px; text-align:left; max-width:480px; margin:0 auto 24px;

}

.conf-row { display:flex; justify-content:space-between; padding:8px 0; border-bottom:1px solid var(--g100); font-size:13px; }

.conf-row:last-child { border-bottom:none; }

.conf-row span  { color:var(--g600); }

.conf-row strong { color:var(--g800); }

.appt-code  { color:var(--blue); font-family:'Courier New',monospace; }

.paid-green { color:var(--green); }

.status-warn { color:var(--amber); }

.next-steps-wrap { max-width:480px; margin:0 auto 24px; text-align:left; }

.next-steps-wrap h4 { font-size:14px; font-weight:700; color:var(--g800); margin:0 0 12px; }

.next-step-row { display:flex; align-items:flex-start; gap:10px; background:var(--g50); border-radius:10px; padding:10px 12px; border:1px solid var(--g100); margin-bottom:8px; }

.ns-ico { font-size:20px; flex-shrink:0; }

.next-step-row strong { font-size:13px; color:var(--g800); display:block; margin-bottom:2px; }

.next-step-row span   { font-size:12px; color:var(--g600); }

.success-btns { display:flex; gap:12px; justify-content:center; flex-wrap:wrap; }



/\* ── RESPONSIVE ────────────────────────────────────── \*/

@media (max-width:600px) {

&#x20; .form-grid   { grid-template-columns:1fr; }

&#x20; .pay-methods { grid-template-columns:repeat(3,1fr); }

&#x20; .step-line   { min-width:16px; }

&#x20; .appt-booking { padding:16px 12px 40px; }

}



/\* VALIDATION TOAST \*/

.val-toast {

&#x20; background: #fef2f2;

&#x20; border: 2px solid #fca5a5;

&#x20; border-radius: 10px;

&#x20; padding: 12px 16px;

&#x20; margin-bottom: 16px;

&#x20; color: #b91c1c;

&#x20; font-size: 13px;

&#x20; font-weight: 600;

&#x20; display: flex;

&#x20; align-items: center;

&#x20; gap: 8px;

&#x20; animation: shake 0.4s ease;

}

@keyframes shake {

&#x20; 0%,100%{transform:translateX(0)}

&#x20; 20%,60%{transform:translateX(-5px)}

&#x20; 40%,80%{transform:translateX(5px)}

}



#### **Client Script**



api.controller=function($timeout) {

&#x20; var c = this;



&#x20; // ── PAGE IDs (confirmed from your ServiceNow Pages list) ──

&#x20; var PAGE\_IDS = {

&#x20;   home:           'test\_catalog',

&#x20;   myAppointments: 'my\_appointments',

&#x20;   labReports:     'lab\_reports'

&#x20; };



&#x20; c.step = 1;

&#x20; c.processing = false;

&#x20; c.errors = {};

&#x20; c.genderOpen = false;

&#x20; c.bankOpen = false;

&#x20; c.testPrice = '0.00';

&#x20; c.validationMsg = '';



&#x20; c.form = {

&#x20;   first\_name: '', last\_name: '', email: '', phone\_number: '',

&#x20;   date\_of\_birth: '', gender: '', address: '',

&#x20;   scheduled\_date: '', slot\_time: '', notes: ''

&#x20; };



&#x20; c.payment = {

&#x20;   method: 'card',

&#x20;   card\_name: '', card\_number: '', expiry: '', cvv: '',

&#x20;   upi\_id: '', upi\_app: '',

&#x20;   bank: '',

&#x20;   insurance\_provider: '', policy\_number: ''

&#x20; };



&#x20; c.genderOptions = \[

&#x20;   { value: 'male',              label: 'Male' },

&#x20;   { value: 'female',            label: 'Female' },

&#x20;   { value: 'other',             label: 'Other' },

&#x20;   { value: 'prefer\_not\_to\_say', label: 'Prefer not to say' }

&#x20; ];



&#x20; c.bankOptions = \[

&#x20;   { value: 'sbi',   label: 'State Bank of India' },

&#x20;   { value: 'hdfc',  label: 'HDFC Bank' },

&#x20;   { value: 'icici', label: 'ICICI Bank' },

&#x20;   { value: 'axis',  label: 'Axis Bank' },

&#x20;   { value: 'kotak', label: 'Kotak Mahindra Bank' },

&#x20;   { value: 'pnb',   label: 'Punjab National Bank' },

&#x20;   { value: 'bob',   label: 'Bank of Baroda' },

&#x20;   { value: 'other', label: 'Other Bank' }

&#x20; ];



&#x20; c.timeSlots = \[

&#x20;   '08:00 AM','08:30 AM','09:00 AM','09:30 AM',

&#x20;   '10:00 AM','10:30 AM','11:00 AM','11:30 AM',

&#x20;   '12:00 PM','12:30 PM','01:00 PM','01:30 PM',

&#x20;   '02:00 PM','02:30 PM','03:00 PM','03:30 PM',

&#x20;   '04:00 PM','04:30 PM','05:00 PM'

&#x20; ];



&#x20; // FIX: padStart() not always available in ServiceNow's JS engine — use manual pad

&#x20; function pad2(n) { return n < 10 ? '0' + n : '' + n; }

&#x20; var today = new Date();

&#x20; c.minDate = today.getFullYear() + '-' + pad2(today.getMonth() + 1) + '-' + pad2(today.getDate());



&#x20; // ── NAVIGATION ────────────────────────────────────────────

&#x20; var \_nav = function(pageId) {

&#x20;   var portalId = window.location.pathname.split('/')\[1] || 'sp';

&#x20;   window.location.href = '/' + portalId + '?id=' + pageId;

&#x20; };



&#x20; // ── INIT ──────────────────────────────────────────────────

&#x20; c.$onInit = function() {

&#x20;   var sysId    = sessionStorage.getItem('selected\_test\_sys\_id')   || '';

&#x20;   var name     = sessionStorage.getItem('selected\_test\_name')     || '';

&#x20;   var price    = sessionStorage.getItem('selected\_test\_price')    || '0';

&#x20;   var code     = sessionStorage.getItem('selected\_test\_code')     || '';

&#x20;   var category = sessionStorage.getItem('selected\_test\_category') || 'General';

&#x20;   var duration = sessionStorage.getItem('selected\_test\_duration') || '';



&#x20;   if (sysId) {

&#x20;     var numPrice = parseFloat(price) || 0;

&#x20;     c.selectedTest = {

&#x20;       sys\_id: sysId, test\_name: name, price: numPrice,

&#x20;       test\_code: code, category: category, test\_duration: duration

&#x20;     };

&#x20;     c.testPrice = numPrice.toFixed(2);

&#x20;     \['selected\_test\_sys\_id','selected\_test\_name','selected\_test\_price',

&#x20;      'selected\_test\_code','selected\_test\_category','selected\_test\_duration']

&#x20;       .forEach(function(k) { sessionStorage.removeItem(k); });

&#x20;   } else if (c.data \&\& c.data.test) {

&#x20;     c.selectedTest = c.data.test;

&#x20;     c.testPrice = (parseFloat(c.data.test.price) || 0).toFixed(2);

&#x20;   }



&#x20;   if (c.data \&\& c.data.currentUser) {

&#x20;     c.form.first\_name   = c.data.currentUser.first\_name || '';

&#x20;     c.form.last\_name    = c.data.currentUser.last\_name  || '';

&#x20;     c.form.email        = c.data.currentUser.email      || '';

&#x20;     c.form.phone\_number = c.data.currentUser.phone      || '';

&#x20;   }

&#x20; };



&#x20; // ── DROPDOWN HELPERS ──────────────────────────────────────

&#x20; c.getGenderLabel = function(val) {

&#x20;   for (var i = 0; i < c.genderOptions.length; i++) {

&#x20;     if (c.genderOptions\[i].value === val) return c.genderOptions\[i].label;

&#x20;   }

&#x20;   return '-- Select Gender --';

&#x20; };

&#x20; c.getBankLabel = function(val) {

&#x20;   for (var i = 0; i < c.bankOptions.length; i++) {

&#x20;     if (c.bankOptions\[i].value === val) return c.bankOptions\[i].label;

&#x20;   }

&#x20;   return '-- Select Bank --';

&#x20; };

&#x20; c.selectGender = function(val) { c.form.gender = val; c.genderOpen = false; c.clearError('gender'); };

&#x20; c.selectBank   = function(val) { c.payment.bank = val; c.bankOpen = false; };

&#x20; c.setPaymentMethod = function(method) { c.payment.method = method; c.bankOpen = false; c.genderOpen = false; };

&#x20; c.selectUpiApp = function(app) { c.payment.upi\_app = app; };



&#x20; // ── MISC HELPERS ──────────────────────────────────────────

&#x20; c.getCategoryIcon = function(cat) {

&#x20;   var icons = {

&#x20;     'blood':'🩸','urine':'🧪','imaging':'🩻','radiology':'🩻',

&#x20;     'cardiology':'❤️','neurology':'🧠','genetics':'🧬','pathology':'🔬',

&#x20;     'biochemistry':'⚗️','allergy':'🌿','microbiology':'🦠','covid':'😷',

&#x20;     'ecg':'❤️','x-ray':'🩻','xray':'🩻','diabetes':'💉','thyroid':'🦋'

&#x20;   };

&#x20;   if (!cat) return '🔬';

&#x20;   var key = cat.toLowerCase();

&#x20;   for (var k in icons) { if (key.indexOf(k) !== -1) return icons\[k]; }

&#x20;   return '🔬';

&#x20; };



&#x20; c.formatDateDisplay = function(dateStr) {

&#x20;   if (!dateStr) return '';

&#x20;   // Normalize: handle both string and Date object

&#x20;   if (typeof dateStr !== 'string') {

&#x20;     try { dateStr = dateStr.toISOString().split('T')\[0]; } catch(e) { return ''; }

&#x20;   }

&#x20;   var parts = dateStr.split('-');

&#x20;   if (parts.length !== 3) return dateStr;

&#x20;   var yr = parseInt(parts\[0], 10);

&#x20;   var mo = parseInt(parts\[1], 10) - 1;

&#x20;   var dy = parseInt(parts\[2], 10);

&#x20;   var d = new Date(yr, mo, dy);

&#x20;   var months = \['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];

&#x20;   var days   = \['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];

&#x20;   return days\[d.getDay()] + ', ' + dy + ' ' + months\[mo] + ' ' + yr;

&#x20; };



&#x20; c.getPaymentLabel = function(method) {

&#x20;   var labels = {

&#x20;     'card':'Credit/Debit Card','upi':'UPI Payment',

&#x20;     'netbanking':'Net Banking','insurance':'Insurance','cash':'Pay on Arrival'

&#x20;   };

&#x20;   return labels\[method] || method;

&#x20; };



&#x20; c.selectSlot = function(slot) { c.form.slot\_time = slot; c.clearError('slot\_time'); };



&#x20; c.onDateChange = function() { c.form.slot\_time = ''; c.clearError('scheduled\_date'); };



&#x20; c.clearError = function(field) {

&#x20;   if (c.errors\[field]) delete c.errors\[field];

&#x20;   c.validationMsg = '';

&#x20; };



&#x20; // ── STEP NAVIGATION (direct — ng-click already triggers digest) ───

&#x20; var \_goToStep = function(n) {

&#x20;   c.step = n;

&#x20;   window.scrollTo(0, 0);

&#x20; };



&#x20; // ── STEP 1 VALIDATION ─────────────────────────────────────

&#x20; c.validateStep1 = function() {

&#x20;   c.errors = {};

&#x20;   c.validationMsg = '';

&#x20;   var f = c.form;

&#x20;   var emailReg = /^\[^\\s@]+@\[^\\s@]+\\.\[^\\s@]+$/;

&#x20;   var phoneReg = /^\\+?\[\\d\\s\\-(). ]{7,20}$/;



&#x20;   if (!f.first\_name || !f.first\_name.trim()) c.errors.first\_name   = 'First name is required';

&#x20;   if (!f.last\_name  || !f.last\_name.trim())  c.errors.last\_name    = 'Last name is required';

&#x20;   if (!f.email      || !f.email.trim())      c.errors.email        = 'Email is required';

&#x20;   else if (!emailReg.test(f.email.trim()))   c.errors.email        = 'Enter a valid email';

&#x20;   if (!f.phone\_number || !f.phone\_number.trim()) c.errors.phone\_number = 'Phone number is required';

&#x20;   else if (!phoneReg.test(f.phone\_number.trim())) c.errors.phone\_number = 'Enter a valid phone number';

&#x20;   if (!f.date\_of\_birth) c.errors.date\_of\_birth = 'Date of birth is required';

&#x20;   if (!f.gender)        c.errors.gender        = 'Please select a gender';



&#x20;   if (Object.keys(c.errors).length > 0) {

&#x20;     c.validationMsg = 'Please fill in all required fields marked below.';

&#x20;     window.scrollTo(0, 0);

&#x20;     return;

&#x20;   }

&#x20;   \_goToStep(2);

&#x20; };



&#x20; // ── STEP 2 VALIDATION ─────────────────────────────────────

&#x20; // KEY FIX: Robust date handling — works with string, Date object, or missing value

&#x20; c.validateStep2 = function() {

&#x20;   c.errors = {};

&#x20;   c.validationMsg = '';



&#x20;   // Normalize the date value safely

&#x20;   var rawDate = c.form.scheduled\_date;

&#x20;   var dateStr = '';



&#x20;   if (rawDate) {

&#x20;     if (typeof rawDate === 'string') {

&#x20;       dateStr = rawDate.trim();

&#x20;     } else if (rawDate instanceof Date) {

&#x20;       // ng-model on type="date" can return a Date object in some AngularJS builds

&#x20;       var yr = rawDate.getFullYear();

&#x20;       var mo = rawDate.getMonth() + 1;

&#x20;       var dy = rawDate.getDate();

&#x20;       dateStr = yr + '-' + pad2(mo) + '-' + pad2(dy);

&#x20;       c.form.scheduled\_date = dateStr; // Normalize to string

&#x20;     } else {

&#x20;       dateStr = String(rawDate).trim();

&#x20;     }

&#x20;   }



&#x20;   if (!dateStr) {

&#x20;     c.errors.scheduled\_date = 'Please select a date';

&#x20;   } else {

&#x20;     try {

&#x20;       var parts = dateStr.split('-');

&#x20;       if (parts.length === 3) {

&#x20;         var sel = new Date(parseInt(parts\[0], 10), parseInt(parts\[1], 10) - 1, parseInt(parts\[2], 10));

&#x20;         var now = new Date();

&#x20;         now.setHours(0, 0, 0, 0);

&#x20;         if (sel < now) c.errors.scheduled\_date = 'Please select a future date';

&#x20;       }

&#x20;     } catch (ex) {

&#x20;       c.errors.scheduled\_date = 'Invalid date selected';

&#x20;     }

&#x20;   }



&#x20;   if (!c.form.slot\_time) {

&#x20;     c.errors.slot\_time = 'Please select a time slot';

&#x20;   }



&#x20;   if (Object.keys(c.errors).length > 0) {

&#x20;     c.validationMsg = 'Please select a date and time slot before continuing.';

&#x20;     window.scrollTo(0, 0);

&#x20;     return;

&#x20;   }



&#x20;   \_goToStep(3);

&#x20; };



&#x20; // ── PAYMENT ───────────────────────────────────────────────

&#x20; c.processPayment = function() {

&#x20;   c.processing = true;

&#x20;   $timeout(function() { c.submitBooking(); }, 1200);

&#x20; };



&#x20; c.submitBooking = function() {

&#x20;   c.server.get({

&#x20;     action: 'create\_appointment',

&#x20;     data: {

&#x20;       form: c.form,

&#x20;       test\_sys\_id: c.selectedTest ? c.selectedTest.sys\_id : '',

&#x20;       payment\_method: c.payment.method,

&#x20;       total\_amount: c.selectedTest ? c.selectedTest.price : 0

&#x20;     }

&#x20;   }).then(function(r) {

&#x20;     c.processing = false;

&#x20;     if (r.data.success) {

&#x20;       c.data.appointmentNumber = r.data.appointment\_number;

&#x20;       \_goToStep(4);

&#x20;     } else {

&#x20;       alert('Error: ' + (r.data.error || 'Something went wrong. Please try again.'));

&#x20;     }

&#x20;   }).catch(function() {

&#x20;     c.processing = false;

&#x20;     alert('Network error. Please try again.');

&#x20;   });

&#x20; };



&#x20; c.prevStep = function() {

&#x20;   if (c.step > 1) \_goToStep(c.step - 1);

&#x20; };



&#x20; c.changeTest         = function() { \_nav(PAGE\_IDS.home); };

&#x20; c.viewMyAppointments = function() { \_nav(PAGE\_IDS.myAppointments); };

&#x20; c.bookAnother        = function() { \_nav(PAGE\_IDS.home); };

}



#### **Server script**

(function() {



&#x20; data.test        = null;

&#x20; data.currentUser = null;

&#x20; data.success     = false;

&#x20; data.error       = '';

&#x20; data.appointmentNumber = '';



&#x20; // ── Safe user detection (no isAnonymous — not allowed in scope) ──

&#x20; try {

&#x20;   var userID   = gs.getUserID()   || '';

&#x20;   var userName = gs.getUserName() || '';



&#x20;   if (userID \&\& userName !== 'guest' \&\& userName !== '') {

&#x20;     var userGr = new GlideRecord('sys\_user');

&#x20;     if (userGr.get(userID)) {

&#x20;       data.currentUser = {

&#x20;         first\_name: userGr.getValue('first\_name')    || '',

&#x20;         last\_name:  userGr.getValue('last\_name')     || '',

&#x20;         email:      userGr.getValue('email')         || '',

&#x20;         phone:      userGr.getValue('mobile\_phone')  || userGr.getValue('phone') || ''

&#x20;       };

&#x20;     }

&#x20;   }

&#x20; } catch(e) {

&#x20;   gs.error('Booking init error: ' + e.message);

&#x20; }



&#x20; // ── Handle appointment creation ──────────────────────────

&#x20; if (input \&\& input.action === 'create\_appointment') {

&#x20;   try {

&#x20;     var formData      = input.data.form        || {};

&#x20;     var testSysId     = input.data.test\_sys\_id || '';

&#x20;     var totalAmount   = parseFloat(input.data.total\_amount) || 0;

&#x20;     var paymentMethod = input.data.payment\_method || 'card';



&#x20;     // Fetch test name \& code for email

&#x20;     var testName = '', testCode = '';

&#x20;     if (testSysId) {

&#x20;       var testGr = new GlideRecord('x\_1989050\_medica\_0\_diagnostic\_test');

&#x20;       if (testGr.get(testSysId)) {

&#x20;         testName = testGr.getValue('test\_name') || '';

&#x20;         testCode = testGr.getValue('test\_code') || '';

&#x20;       }

&#x20;     }



&#x20;     // ── Find or create PATIENT record (not sys\_user!) ────

&#x20;     var patientSysId = '';

&#x20;     var patGr = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;     patGr.addQuery('email', formData.email || '');

&#x20;     patGr.setLimit(1);

&#x20;     patGr.query();



&#x20;     if (patGr.next()) {

&#x20;       // Update existing patient

&#x20;       patientSysId = patGr.getUniqueValue();

&#x20;       patGr.setValue('first\_name',   formData.first\_name   || '');

&#x20;       patGr.setValue('last\_name',    formData.last\_name    || '');

&#x20;       patGr.setValue('phone\_number', formData.phone\_number || '');

&#x20;       patGr.setValue('address',      formData.address      || '');

&#x20;       patGr.update();

&#x20;     } else {

&#x20;       // Create new patient record

&#x20;       var newPat = new GlideRecord('x\_1989050\_medica\_0\_patient');

&#x20;       newPat.initialize();

&#x20;       newPat.setValue('first\_name',    formData.first\_name    || '');

&#x20;       newPat.setValue('last\_name',     formData.last\_name     || '');

&#x20;       newPat.setValue('email',         formData.email         || '');

&#x20;       newPat.setValue('phone\_number',  formData.phone\_number  || '');

&#x20;       newPat.setValue('date\_of\_birth', formData.date\_of\_birth || '');

&#x20;       newPat.setValue('gender',        formData.gender        || '');

&#x20;       newPat.setValue('address',       formData.address       || '');



&#x20;       // Link to sys\_user if logged in

&#x20;       var uid = gs.getUserID();

&#x20;       if (uid \&\& gs.getUserName() !== 'guest') {

&#x20;         newPat.setValue('user', uid);

&#x20;       }

&#x20;       patientSysId = newPat.insert();

&#x20;     }



&#x20;     if (!patientSysId) {

&#x20;       data.error = 'Failed to create patient record. Check table ACLs.';

&#x20;       return;

&#x20;     }



&#x20;     // ── Create appointment ────────────────────────────────

&#x20;     var apptNum = 'APPT-' + new Date().getFullYear() + '-' +

&#x20;                   (Math.floor(Math.random() \* 90000) + 10000);



&#x20;     var apptGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;     apptGr.initialize();

&#x20;     apptGr.setValue('appointment\_number', apptNum);

&#x20;     apptGr.setValue('patient',            patientSysId);  // links to patient table

&#x20;     apptGr.setValue('test',               testSysId);     // links to diagnostic test

&#x20;     apptGr.setValue('status',             'pending');

&#x20;     apptGr.setValue('approval\_status',    'requested');

&#x20;     apptGr.setValue('payment\_status',     'paid');

&#x20;     apptGr.setValue('total\_amount',       totalAmount);

&#x20;     apptGr.setValue('scheduled\_date',     formData.scheduled\_date || '');

&#x20;     apptGr.setValue('slot\_time',          formData.slot\_time      || '');

&#x20;     apptGr.setValue('notes',              formData.notes          || '');

&#x20;     apptGr.setValue('confirmation\_sent',  false);

&#x20;     apptGr.setValue('email',              formData.email || '');  // ← NEW: Save email to appointment table



&#x20;     var uid2 = gs.getUserID();

&#x20;     if (uid2 \&\& gs.getUserName() !== 'guest') {

&#x20;       apptGr.setValue('created\_by', uid2);

&#x20;     }



&#x20;     var apptSysId = apptGr.insert();

&#x20;     if (!apptSysId) {

&#x20;       data.error = 'Failed to create appointment. Check table permissions.';

&#x20;       return;

&#x20;     }



&#x20;     // ── Patient confirmation email ────────────────────────

&#x20;     try {

&#x20;       var patEmail = new GlideEmailOutbound();

&#x20;       patEmail.setTo(formData.email);

&#x20;       patEmail.setSubject('Appointment Confirmed: ' + apptNum + ' — MediCare Diagnostic Center');

&#x20;       patEmail.setBody(

&#x20;         '<div style="font-family:Arial,sans-serif;max-width:600px;margin:0 auto;">' +

&#x20;         '<div style="background:#0a2463;padding:24px;text-align:center;border-radius:12px 12px 0 0;">' +

&#x20;         '<h2 style="color:#fff;margin:0;">🏥 MediCare Diagnostic Center</h2></div>' +

&#x20;         '<div style="background:#f0fdf4;border:2px solid #10b981;border-radius:0 0 12px 12px;padding:24px;">' +

&#x20;         '<h3 style="color:#065f46;">✅ Booking Confirmed!</h3>' +

&#x20;         '<p>Dear ' + (formData.first\_name||'') + ' ' + (formData.last\_name||'') + ',</p>' +

&#x20;         '<table style="width:100%;font-size:14px;border-collapse:collapse;background:#fff;border-radius:8px;">' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Appointment #</td><td style="padding:10px;">' + apptNum + '</td></tr>' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Test</td><td style="padding:10px;">' + testName + ' (' + testCode + ')</td></tr>' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Date</td><td style="padding:10px;">' + (formData.scheduled\_date||'') + '</td></tr>' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Time</td><td style="padding:10px;">' + (formData.slot\_time||'') + '</td></tr>' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Amount Paid</td><td style="padding:10px;color:#10b981;font-weight:700;">$' + totalAmount.toFixed(2) + '</td></tr>' +

&#x20;         '<tr><td style="padding:10px;background:#f8fafc;font-weight:600;">Payment</td><td style="padding:10px;">' + paymentMethod + '</td></tr>' +

&#x20;         '</table>' +

&#x20;         '<p style="margin-top:16px;color:#6b7280;font-size:13px;">Pending admin approval. You will receive a confirmation within 24 hours.</p>' +

&#x20;         '</div></div>'

&#x20;       );

&#x20;       patEmail.save();

&#x20;     } catch(emailErr) { gs.warn('Patient email error: ' + emailErr.message); }



&#x20;     // ── Admin approval email ──────────────────────────────

&#x20;     try {

&#x20;       var adminEmail = gs.getProperty('medicare.admin.email', '');

&#x20;       if (adminEmail) {

&#x20;         var adminMail = new GlideEmailOutbound();

&#x20;         adminMail.setTo(adminEmail);

&#x20;         adminMail.setSubject('\[Action Required] New Appointment: ' + apptNum);

&#x20;         adminMail.setBody(

&#x20;           '<div style="font-family:Arial,sans-serif;max-width:600px;">' +

&#x20;           '<div style="background:#0a2463;padding:20px;border-radius:8px 8px 0 0;"><h2 style="color:#fff;margin:0;">New Appointment — Approval Required</h2></div>' +

&#x20;           '<div style="background:#fffbeb;border:2px solid #f59e0b;border-radius:0 0 8px 8px;padding:24px;">' +

&#x20;           '<table style="width:100%;font-size:14px;border-collapse:collapse;">' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;width:40%;">Appointment #</td><td style="padding:8px;">' + apptNum + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Patient</td><td style="padding:8px;">' + (formData.first\_name||'') + ' ' + (formData.last\_name||'') + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Email</td><td style="padding:8px;">' + (formData.email||'') + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Phone</td><td style="padding:8px;">' + (formData.phone\_number||'') + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Test</td><td style="padding:8px;">' + testName + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Date \&amp; Time</td><td style="padding:8px;">' + (formData.scheduled\_date||'') + ' ' + (formData.slot\_time||'') + '</td></tr>' +

&#x20;           '<tr><td style="padding:8px;font-weight:600;">Amount</td><td style="padding:8px;color:#059669;font-weight:700;">$' + totalAmount.toFixed(2) + '</td></tr>' +

&#x20;           '</table>' +

&#x20;           '<div style="margin-top:20px;padding:12px;background:#f1f5f9;border-radius:8px;font-size:13px;color:#475569;">To approve or reject: open the appointment record in ServiceNow backend and change the <strong>Approval Status</strong> field.</div>' +

&#x20;           '</div></div>'

&#x20;         );

&#x20;         adminMail.save();

&#x20;       }

&#x20;     } catch(admErr) { gs.warn('Admin email error: ' + admErr.message); }



&#x20;     // Mark confirmation sent

&#x20;     var cfGr = new GlideRecord('x\_1989050\_medica\_0\_appointment\_table');

&#x20;     if (cfGr.get(apptSysId)) {

&#x20;       cfGr.setValue('confirmation\_sent', true);

&#x20;       cfGr.update();

&#x20;     }



&#x20;     data.success            = true;

&#x20;     data.appointment\_number = apptNum;

&#x20;     data.appointment\_sys\_id = apptSysId;



&#x20;   } catch(submitErr) {

&#x20;     gs.error('Create Appointment Error: ' + submitErr.message);

&#x20;     data.error = submitErr.message;

&#x20;   }

&#x20; }



})();

