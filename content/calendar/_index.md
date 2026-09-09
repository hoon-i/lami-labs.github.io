---
title: Calendar
date: 2024-01-01
type: landing
url: /calendar/

design:
  spacing: "4rem"

sections:
  - block: markdown
    id: calendar
    content:
      title: Appointments
      text: |
        <style>
          #calendar .max-w-prose,
          #calendar .prose {
            max-width: min(1100px, 96vw) !important;
            width: 100% !important;
          }

          .cal-embed-wrap {
            width: 100%;
            border-radius: 0.75rem;
            overflow: hidden;
            border: 1px solid #e2e8f0;
            margin-bottom: 1.25rem;
          }

          .cal-embed-wrap iframe {
            display: block;
            width: 100%;
            height: 640px;
            border: none;
          }

          .cal-notice {
            font-size: 0.92rem;
            line-height: 1.7;
            color: #475569;
            background: #f8fafc;
            border-left: 3px solid #2b2b2b;
            border-radius: 0 0.5rem 0.5rem 0;
            padding: 0.75rem 1rem;
            margin-bottom: 2rem;
          }
          .dark .cal-notice {
            background: #1e293b;
            color: #94a3b8;
          }
          .cal-notice strong { color: #2b2b2b; }
          .dark .cal-notice strong { color: #e5e5e5; }

          .cal-section-title {
            font-size: 2rem;
            font-weight: 700;
            margin-top: 2.5rem;
            margin-bottom: 1rem;
            text-align: center;
          }
        </style>

        <div class="cal-notice">
          <strong>[중요]</strong> 페이지 하단의 캘린더를 확인하시고, 기존 일정(바쁨)과 <strong>30분 이상 간격</strong>을 두고 예약해 주세요.<br>
          <strong>[Important]</strong> Please check the calendar at the bottom of this page and schedule your appointment at least <strong>30 minutes</strong> apart from any existing (busy) events.
        </div>

        <div class="cal-embed-wrap">
          <iframe
            src="https://calendar.google.com/calendar/appointments/schedules/AcZssZ3fwwko_EDc5hJ9Vq_n8ZSI7apGjGm0oFzRsmUOptHHUyVw0TH6jvU_0b6jlHYveYtRYfCCl-od?gv=true"
            frameborder="0"
            scrolling="yes"
            style="height: 700px;"
            allowfullscreen>
          </iframe>
        </div>

        <h2 class="cal-section-title">Calendar</h2>

        <div class="cal-embed-wrap">
          <iframe
            src="https://www.google.com/calendar/embed?color=%239fe1e7&embed_style=WyJhdDplbWI6c3QiLCIjZTBlMGUwIiwiI2VkZWRlZCIsIiM0MTg0ZjMiLCJyb2JvdG8iLCIjNjM2MzYzIiw1MDAsIiNmZmYiXQo&eopt=2&mode=week&showCalendars=1&showPrint=0&showTabs=0&showTitle=0&showTz=1&src=YOUR_CALENDAR@gmail.com"
            frameborder="0"
            scrolling="no"
            style="height: 480px;"
            allowfullscreen>
          </iframe>
        </div>
    design:
      spacing:
        padding: ["3rem", 0, "3rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
---
