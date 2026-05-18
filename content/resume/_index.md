---
title: 'Resume'
date: 2025-01-01
type: landing

design:
  spacing: '4rem'

sections:
  - block: markdown
    content:
      title: 'Curriculum Vitae'
      subtitle: ''
      text: |
        A rendered overview of my CV is shown below. You can also
        <a class="font-semibold underline" href="/uploads/CV_FGenans_DS.pdf" download>download the full PDF</a>.

        <div class="my-4 flex flex-wrap gap-3">
          <a href="/uploads/CV_FGenans_DS.pdf" download
             class="inline-flex items-center px-5 py-2.5 rounded-md bg-primary-600 hover:bg-primary-700 text-white font-medium shadow-sm transition">
            ⬇ Download CV (PDF)
          </a>
          <a href="/uploads/CV_FGenans_DS.pdf" target="_blank" rel="noopener"
             class="inline-flex items-center px-5 py-2.5 rounded-md border border-gray-300 dark:border-gray-600 hover:bg-gray-50 dark:hover:bg-gray-800 font-medium transition">
            ↗ Open in new tab
          </a>
        </div>
    design:
      columns: '1'

  - block: resume-experience
    content:
      username: admin
    design:
      date_format: 'January 2006'
      is_education_first: false

  - block: resume-skills
    content:
      title: 'Skills'
      username: admin
    design:
      show_skill_percentage: false

  - block: resume-awards
    content:
      title: 'Awards'
      username: admin

  - block: resume-languages
    content:
      title: 'Languages'
      username: admin

  - block: markdown
    content:
      title: 'CV (PDF preview)'
      subtitle: ''
      text: |
        <div class="w-full rounded-lg overflow-hidden shadow border border-gray-200 dark:border-gray-700">
          <object data="/uploads/CV_FGenans_DS.pdf#view=FitH" type="application/pdf"
                  class="w-full" style="height: 90vh; min-height: 600px;">
            <p class="p-4">
              Your browser cannot display the embedded PDF.
              <a class="underline font-semibold" href="/uploads/CV_FGenans_DS.pdf" download>Download the CV here</a>.
            </p>
          </object>
        </div>
    design:
      columns: '1'
---
