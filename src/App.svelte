<script lang="ts">
    import FlashCard from "./lib/FlashCard.svelte";

    // Define flash cards data structure
    const flashCards = [
        // Unit 6
        { id: 1, question: "brave", answer: "dapper" },
        { id: 2, question: "generous", answer: "gul" },
        { id: 3, question: "honest", answer: "eerlijk" },
        { id: 4, question: "kind", answer: "lief" },
        { id: 5, question: "lazy", answer: "lui" },
        { id: 6, question: "quiet", answer: "rustig" },
        { id: 7, question: "shy", answer: "verlegen" },
        { id: 8, question: "dishonest", answer: "oneerlijk" },
        { id: 9, question: "extroverted", answer: "extravert" },
        { id: 10, question: "hard-working", answer: "ijverig" },
        { id: 11, question: "unkind", answer: "onaardig" },
        { id: 12, question: "mean", answer: "gemeen" },
        { id: 13, question: "serious", answer: "ernstig" },
        { id: 14, question: "talkative", answer: "praatziek" },
        { id: 15, question: "cowardly", answer: "laf" },
        { id: 16, question: "get into trouble", answer: "in de problemen raken" },
        { id: 17, question: "arrest", answer: "arresteren" },
        { id: 18, question: "punish", answer: "straffen" },
        { id: 19, question: "(pay a) fine", answer: "een boete betalen" },
        { id: 20, question: "(appear in) court", answer: "voor de rechtbank verschijnen" },
        { id: 21, question: "commit (a crime)", answer: "een misdaad begaan" },
        { id: 22, question: "charge", answer: "beschuldigen" },
        { id: 23, question: "(spend time in) prison", answer: "een gevangenisstraf uitzitten" },
        { id: 24, question: "happy", answer: "gelukkig" },
        { id: 25, question: "unhappy", answer: "ongelukkig" },
        { id: 26, question: "responsible", answer: "verantwoordelijk" },
        { id: 27, question: "irresponsible", answer: "onverantwoordelijk" },
        { id: 28, question: "unthinkable", answer: "ondenkbaar" },
        { id: 29, question: "legal", answer: "wettelijk" },
        { id: 30, question: "illegal", answer: "onwettelijk" },
        //{ id: 31, question: "polite", answer: "beleefd" },
        //{ id: 32, question: "impolite", answer: "onbeleefd" },
        //{ id: 33, question: "possible", answer: "mogelijk" },
        //{ id: 34, question: "impossible", answer: "onmogelijk" },
        //{ id: 35, question: "usual", answer: "gewoon" },
        //{ id: 36, question: "unusual", answer: "ongewoon" },
        //{ id: 37, question: "mature", answer: "volwassen" },
        //{ id: 38, question: "immature", answer: "onvolwassen" },
        //{ id: 39, question: "perfect", answer: "perfect" },
        //{ id: 40, question: "imperfect", answer: "onvolmaakt" },
        //{ id: 41, question: "rational", answer: "rationeel" },
        //{ id: 42, question: "irrational", answer: "irrationeel" },
        //{ id: 43, question: "literate", answer: "geletterd" },
        //{ id: 44, question: "illiterate", answer: "ongeletterd" },
        //{ id: 45, question: "warm", answer: "warm" },
        //{ id: 46, question: "blue", answer: "blauw" },
        //{ id: 47, question: "narrow", answer: "smal" },
        //{ id: 48, question: "grey", answer: "grijs" },
        //{ id: 49, question: "sweet-scented", answer: "geurig" },
        //{ id: 50, question: "drab", answer: "saai" },
        //{ id: 51, question: "cold", answer: "koud" },
        //{ id: 52, question: "green", answer: "groen" },
        //{ id: 53, question: "glass-clear", answer: "glashelder" },
        //{ id: 54, question: "bully", answer: "pesten" },
        //{ id: 55, question: "cheat", answer: "vals spelen" },
        //{ id: 56, question: "expel", answer: "van school sturen" },
        //{ id: 57, question: "fight", answer: "vechten" },
        //{ id: 58, question: "(give a) detention", answer: "laten nablijven" },
        //{ id: 59, question: "(give a) warning", answer: "waarschuwen" },
        //{ id: 60, question: "play truant", answer: "spijbelen" },
        //{ id: 61, question: "suspend", answer: "schorsen" },
        //{ id: 62, question: "swear", answer: "vloeken" },
        //{ id: 63, question: "vandalize", answer: "plunderen" },
        //{ id: 64, question: "classroom", answer: "klaslokaal" },
        //{ id: 65, question: "head teacher", answer: "schoolhoofd" },
        //{ id: 66, question: "noticeboard", answer: "prikbord" },
        //{ id: 67, question: "playground", answer: "speelplaats" },
        //{ id: 68, question: "playing field", answer: "sportterrein" },
        //{ id: 69, question: "school canteen", answer: "schoolkantine" },
        //{ id: 70, question: "school uniform", answer: "schooluniform" },
        //{ id: 71, question: "science laboratory", answer: "wetenschappelijk laboratorium" },
        //{ id: 72, question: "sports hall", answer: "sportzaal" },
        //{ id: 73, question: "staffroom", answer: "leraarskamer" },
        //{ id: 74, question: "textbook", answer: "handboek" },
        //{ id: 75, question: "timetable", answer: "lesrooster" },
        //{ id: 76, question: "increase", answer: "stijgen" },
        //{ id: 77, question: "estimate", answer: "schatten" },
        //{ id: 78, question: "double", answer: "verdubbelen" },
        //{ id: 79, question: "multiply", answer: "vermenigvuldigen" },
        //{ id: 80, question: "calculate", answer: "berekenen" },
        //{ id: 81, question: "decrease", answer: "dalen" },
    ];

    // Create a shuffled version of the flashcards
    let shuffledCards = [];

    // Fisher-Yates shuffle algorithm function
    function shuffleArray(array: any) {
        // Create a copy of the original array to avoid modifying it
        const arrayCopy = [...array];
        // Start from the last element and swap it with a randomly selected element
        for (let i = arrayCopy.length - 1; i > 0; i--) {
            // Pick a random index from 0 to i
            const j = Math.floor(Math.random() * (i + 1));
            // Swap elements at i and j
            [arrayCopy[i], arrayCopy[j]] = [arrayCopy[j], arrayCopy[i]];
        }
        return arrayCopy;
    }

    // Initialize shuffled cards when component loads
    shuffledCards = shuffleArray(flashCards);

    // Keep track of the current card index
    let currentCardIndex = 0;

    // State for tracking points system
    let points = 0;
    let attempted = 0;

    // Function to go to the next card
    // Function to go to the next card
    function nextCard() {
        if (currentCardIndex < shuffledCards.length - 1) {
            currentCardIndex++;
        }
    }

    // Function to go to the previous card
    function prevCard() {
        if (currentCardIndex > 0) {
            currentCardIndex--;
        }
    }
    // Function to update points when an answer is submitted
    function handleAnswerSubmit(event: any) {
        const isCorrect = event.detail.isCorrect;
        attempted++;

        if (isCorrect) {
            points++; // Add 1 point for correct answer

            // Set a 2-second delay for correct answers before moving to the next card
            if (currentCardIndex < shuffledCards.length - 1) {
                setTimeout(() => {
                    nextCard();
                }, 2000);
            }
        } else {
            // No point deduction for incorrect answers

            // Set a 5-second delay for incorrect answers before moving to the next card
            if (currentCardIndex < shuffledCards.length - 1) {
                setTimeout(() => {
                    nextCard();
                }, 5000);
            }
        }
    }
</script>

<main>
    <div class="container">
        <h1>Engels woordenschat</h1>

        <div class="score-container">
            <p>Points: {points} (Attempted: {attempted})</p>
        </div>

        <div class="card-container">
            <FlashCard
                flashCard={shuffledCards[currentCardIndex]}
                on:answerSubmitted={handleAnswerSubmit}
            />
        </div>

        <div class="navigation">
            <button on:click={prevCard} disabled={currentCardIndex === 0}
                >Previous</button
            >
            <span class="card-counter"
                >{currentCardIndex + 1} / {shuffledCards.length}</span
            >
            <button
                on:click={nextCard}
                disabled={currentCardIndex === shuffledCards.length - 1}
                >Next</button
            >
        </div>
    </div>
</main>

<style>
    :global(body) {
        background-color: #10abb4;
        color: #004c50;
        margin: 0;
        padding: 0;
        font-family:
            -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans,
            Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
    }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        max-width: 800px;
        margin: 0 auto;
        padding: 20px;
        background-color: white;
        border-radius: 12px;
        box-shadow: 0 4px 12px rgba(0, 76, 80, 0.1);
    }

    h1 {
        color: #004c50;
        margin-bottom: 20px;
        font-weight: 700;
        text-align: center;
    }

    .score-container {
        margin-bottom: 20px;
        font-size: 1.2rem;
        font-weight: bold;
        color: #004c50;
        background-color: rgba(16, 171, 180, 0.1);
        padding: 8px 16px;
        border-radius: 8px;
    }

    .card-container {
        width: 100%;
        margin-bottom: 20px;
    }

    .navigation {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        max-width: 400px;
        padding: 10px;
        background-color: rgba(0, 147, 156, 0.05);
        border-radius: 8px;
    }

    button {
        background-color: #00939c;
        color: white;
        border: none;
        padding: 10px 20px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
        border-radius: 4px;
        transition: all 0.3s ease;
        font-weight: 500;
        box-shadow: 0 2px 4px rgba(0, 76, 80, 0.2);
    }

    button:hover {
        background-color: #10abb4;
        transform: translateY(-2px);
        box-shadow: 0 4px 8px rgba(0, 76, 80, 0.3);
    }

    button:disabled {
        background-color: rgba(0, 147, 156, 0.3);
        cursor: not-allowed;
        box-shadow: none;
        transform: none;
    }

    .card-counter {
        font-size: 1rem;
        color: #502000;
        font-weight: 600;
        background-color: rgba(156, 62, 0, 0.1);
        padding: 4px 10px;
        border-radius: 4px;
    }
</style>
