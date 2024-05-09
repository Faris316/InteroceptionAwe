# InteroceptionAwe
<!DOCTYPE html>
<html>
  <head>
    <title>My experiment</title>
    <script src="jspsych/jspsych.js"></script>
    <script src="jspsych/plugin-html-button-response.js"></script>
    <script src="jspsych/plugin-html-keyboard-response.js"></script>
    <script src="jspsych/plugin-survey-multi-choice.js"></script>
    <script src="jspsych/plugin-survey-likert.js"></script>
    <link href="jspsych/jspsych.css" rel="stylesheet" type="text/css" />
  </head>
  <body></body>
  <script>
    const jsPsych = initJsPsych();

    var timeline = []

    var demographics_consent_incentivized = {
    type: jsPsychHtmlButtonResponse,
    stimulus:
        // Logo and title
        "<img src='https://blogs.brighton.ac.uk/sussexwrites/files/2019/06/University-of-Sussex-logo-transparent.png' width='150px' align='right'/><br><br><br><br><br>" +
        "<h1>Informed Consent</h1>" +
        // Overview
        "<p align='left'><b>Invitation to Take Part</b><br>" +
        "You are being invited to take part in a research study to further our understanding of Human psychology. Thank you for carefully reading this information sheet. This study is being conducted by Dr Dominique Makowski from the School of Psychology, University of Sussex, who is happy to be contacted (D.Makowski@sussex.ac.uk) if you have any questions.</p>" +
        // Description
        "<p align='left'><b>Why have I been invited and what will I do?</b><br>" +
        "We are surveying adults to understand how mood fluctuations and mood disorders symptoms (or absence thereof) are expressed and what difficulties they can generate. This study contains various questionnaires about your personality, feelings and current state of mind. The whole experiment will take you <b>about 10 min</b> to complete. Please make you sure that you are in a quiet environment, and that you have time to complete it in one go.</p>" +
        // Results and personal information
        "<p align='left'><b>What will happen to the results and my personal information?</b><br>" +
        "The results of this research may be written into a scientific publication. Your anonymity will be ensured in the way described in the consent information below. Please read this information carefully and then, if you wish to take part, please acknowledge that you have fully understood this sheet, and that you consent to take part in the study as it is described here.</p>" +
        "<p align='left'><b>Consent</b><br></p>" +
        // Bullet points
        "<li align='left'>I understand that by signing below I am agreeing to take part in the University of Sussex research described here, and that I have read and understood this information sheet</li>" +
        "<li align='left'>I understand that my participation is entirely voluntary, that I can choose not to participate in part or all of the study, and that I can withdraw at any stage by closing the browser without having to give a reason and without being penalised in any way (e.g., if I am a student, my decision whether or not to take part will not affect my grades).</li>" +
        "<li align='left'>I understand that since the study is anonymous, it will be impossible to withdraw my data once I have completed and submitted the test/questionnaire.</li>" +
        "<li align='left'>I understand that my personal data will be used for the purposes of this research study and will be handled in accordance with Data Protection legislation. I understand that the University's Privacy Notice provides further information on how the University uses personal data in its research.</li>" +
        "<li align='left'>I understand that my collected data will be stored in a de-identified way. De-identified data may be made publically available through secured scientific online data repositories.</li>" +
        // Incentive
        "<li align='left'>Please note that various checks will be performed to ensure the validity of the data. We reserve the right to withhold credit awards or reimbursement (if applicable) should we detect non-valid responses (e.g., random patterns of answers, instructions not read, ...).</li>" +
        "<li align='left'>By participating, you agree to follow the instructions and provide honest answers. If you do not wish to participate, simply close your browser.</li>" +
        "</p>" +
        "<p align='left'><br><sub><sup>For further information about this research, or if you have any concerns, please contact Dr Dominique Makowski (D.Makowski@sussex.ac.uk). This research has been approved (ER/NAAA21/1) by the ethics board of the School of Psychology. The University of Sussex has insurance in place to cover its legal liabilities in respect of this study.</sup></sub></p>",
    choices: ["I read, understood, and I consent"],
    data: { screen: "consent" },
}
    var consent_form = {
        type: jsPsychHtmlButtonResponse,
        stimulus: '<p>By participating in this study, you agree to the following:</p>' +
            '<p>- You are at least 18 years old.</p>' +
            '<p>- Participation is voluntary and you can withdraw at any time.</p>' +
            '<p>- Your responses will be kept confidential and anonymous.</p>' +
            '<p>- The study involves watching videos and completing questionnaires.</p>' +
            '<p>Please click "I agree" to proceed.</p>',
        choices: ["I agree"],
        post_trial_gap: 500
    };
   timeline.push(consent_form)

    var demographic_questionnaire = {
        type: jsPsychSurveyMultiChoice,
        questions: [
            {prompt: "What is your age?", options: ["Under 18", "18-24", "25-34", "35-44", "45-54", "55-64", "65 or older"]},
            {prompt: "What is your gender?", options: ["Male", "Female", "Other", "Prefer not to say"]},
            {prompt: "What is your highest level of education?", options: ["High school or less", "Some college", "Bachelor's degree", "Master's degree", "Doctorate", "Other"]}
        ]
    };

    var bhs_questionnaire = {
        type: jsPsychSurveyMultiChoice,
        questions: [
    {"prompt": "I look forward to the future with hope and enthusiasm.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I can't imagine what my life would be like in ten years.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that there is no hope for the future.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I'm filled with a sense of hopelessness.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that the future is bleak and without hope.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that things are getting worse and worse for me.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I don't expect to get what I really want in the future.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel powerless to change my life for the better.", "options": ["TRUE", "FALSE"]},
    {"prompt": "There's no use in really trying to get something I want because I probably won't get it.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm not really worth much as a person.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I have nothing to look forward to.", "options": ["TRUE", "FALSE"]},
    {"prompt": "The future seems to me to be vague and uncertain.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I'm afraid of what the future holds for me.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I'm getting more and more worried about what the future holds for me.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I don't really expect things to work out for me.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I just don't get the breaks that I should.", "options": ["TRUE", "FALSE"]},
    {"prompt": "Things just won't work out the way I want them to.", "options": ["TRUE", "FALSE"]},
    {"prompt": "The future seems dark to me.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that the future is hopeless and that things cannot improve.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm being punished.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I wonder why I am even alive.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I wonder if my family would be better off if I were dead.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I don't have anything to be proud of.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel like a failure.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm worthless.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm a bad person.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm not good-looking.", "options": ["TRUE", "FALSE"]},
    {"prompt": "I feel that I'm not as good as most people.", "options": ["TRUE", "FALSE"]}
        ],
        preamble: "<p>Beck Hopelessness Scale (BHS): The following is a self-report inventory designed to measure levels of hopelessness. Please answer each question by circling true or false based on how you have been feeling in the past weeks, including today.</p>",
        scale_width: 400,
        button_label: "Next",
        randomize_question_order: true,
        randomize_choices: true
    };

    var rrs_questionnaire = {
        type: jsPsychSurveyLikert,
        questions: [
    {"prompt": "I think about how sad I feel.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about a recent situation, wishing it had gone better or I had handled it better.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about all the things I have to do.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about my feelings of inadequacy.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about how hard it is to concentrate.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about my feelings of loneliness.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about why I feel this way.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about the fact that I can't get the thoughts out of my mind.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about my feelings of fatigue.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about my feelings of worthlessness.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about my problems, analyzing them from every angle.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about how much I dislike myself.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about things that I have done or should have done differently.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about all the things I am doing wrong.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]},
    {"prompt": "I think about how alone I feel in the world.", "options": ["Almost never", "Sometimes", "Often", "Almost always"]}
],
        preamble: "<p>Ruminative Response Scale (RRS): Please rate how frequently you respond in the following ways.</p>",
        button_label: "Next"
    };

    var awe_experience_questionnaire = {
        type: jsPsychSurveyLikert,
        questions: [
    {"prompt": "I sensed things momentarily slow down.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I noticed time slowing.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt my sense of time change.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I experienced the passage of time differently.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I had the sense that a moment lasted longer than usual.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt that my sense of self was diminished.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt my sense of self shrink.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I experienced a reduced sense of self.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt my sense of self become somehow smaller.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt small compared to everything else.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I had the sense of being connected to everything.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt a sense of communion with all living things.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I experienced a sense of oneness with all things.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt closely connected to humanity.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I had a sense of complete connectedness.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt that I was in the presence of something grand.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I experienced something greater than myself.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt in the presence of greatness.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I perceived something that was much larger than me.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I perceived vastness.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt my jaw drop.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I had goosebumps.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I gasped.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I had chills.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt my eyes widen.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt challenged to mentally process what I was experiencing.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I found it hard to comprehend the experience in full.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I felt challenged to understand the experience.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I struggled to take in all that I was experiencing at once.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]},
    {"prompt": "I tried to understand the magnitude of what I was experiencing.", "options": ["Strongly Disagree", "Moderately Disagree", "Somewhat Disagree", "Neutral", "Somewhat Agree", "Moderately Agree", "Strongly Agree"]}
],
        preamble: "<p>Awe-experience scale (AWE-S): Please rate your experience of awe during the video.</p>",
        button_label: "Next"
    };

    var interoception_questionnaire = {
        type: jsPsychSurveyLikert,
        questions: [
            {prompt: "I notice when my heart rate increases", labels: ["Not at all", "Slightly", "Moderately", "Very much"]}
        ],
        preamble: "<p>Interoception questionnaire (Control group): Please rate your awareness of bodily sensations.</p>",
        button_label: "Next"
    };

    var sts_questionnaire = {
        type: jsPsychSurveyLikert,
        questions: [
    {"prompt": "Having hobbies or interests I can enjoy", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Accepting myself as I grow older.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Being involved with other people or my community when possible", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Adjusting well to my present life situation.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Adjusting to the changes in my physical ability.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Sharing my wisdom or experience with others.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Finding meaning in my past experiences.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Helping younger people or others in some way.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Having an interest in continuing to learn about things.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Putting aside some things that I once thought were so important.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Accepting death as a part of life.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Finding meaning in my spiritual beliefs.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Letting others help me when I may need it.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Enjoying my pace of life.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]},
    {"prompt": "Dwelling on my past unmet dreams or goals.", "options": ["1=Not at all", "2=Very little", "3=Somewhat", "4=Very much"]}
    ],
        preamble: "<p>Self-transcendence scale (STS): Please rate how often you experience certain thoughts, feelings, and behaviors.</p>",
        button_label: "Finish"
    };

    jsPsych.run(timeline);
</script>
</html>