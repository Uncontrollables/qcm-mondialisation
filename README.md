# qcm-mondialisation
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QCM - Échanges et Mondialisation</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
        }
    </style>
</head>
<body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen">
    <div id="root"></div>

    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <script type="text/babel">
        const { useState } = React;

        const CheckIcon = () => (
            <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M5 13l4 4L19 7" />
            </svg>
        );

        const XIcon = () => (
            <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M6 18L18 6M6 6l12 12" />
            </svg>
        );

        const RefreshIcon = () => (
            <svg className="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
            </svg>
        );

        const AwardIcon = () => (
            <svg className="w-24 h-24" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
            </svg>
        );

        const QCMMondialisation = () => {
            const questions = [
                {
                    id: 1,
                    question: "Qu'est-ce que la mondialisation selon le cours ?",
                    options: [
                        "Uniquement l'augmentation des échanges commerciaux",
                        "L'intégration croissante des économies par des flux de biens, services, capitaux et personnes",
                        "La domination économique des pays riches",
                        "L'harmonisation des cultures mondiales"
                    ],
                    correct: 1,
                    explication: "La mondialisation décrit l'intégration croissante des économies du monde par des flux grandissants de biens, de services, de capitaux et de personnes au-delà des frontières nationales."
                },
                {
                    id: 2,
                    question: "Quelles sont les trois grandes périodes de la mondialisation des biens et services ?",
                    options: [
                        "Expansion, Stabilisation, Déclin",
                        "Mondialisation (1840-1914), Démondialisation (1914-1945), Remondialisation (1945-2020)",
                        "Croissance, Crise, Reprise",
                        "Industrialisation, Tertiarisation, Numérisation"
                    ],
                    correct: 1,
                    explication: "Le cours identifie trois grandes périodes : Mondialisation (1840-1914) avec chemins de fer et empires coloniaux, Démondialisation (1914-1945) avec protectionnisme, et Remondialisation (1945-2020) avec libéralisation."
                },
                {
                    id: 3,
                    question: "Quel facteur de production n'a PAS connu de remondialisation ?",
                    options: [
                        "Les capitaux",
                        "Les biens manufacturés",
                        "Le travail",
                        "Les services"
                    ],
                    correct: 2,
                    explication: "Contrairement aux biens, services et capitaux, le facteur travail n'a pas connu de remondialisation. Les restrictions à la libre circulation des personnes sont globalement plus limitées aujourd'hui qu'en 1913."
                },
                {
                    id: 4,
                    question: "Qu'est-ce qu'un avantage comparatif ?",
                    options: [
                        "Être le plus performant dans la production d'un bien",
                        "Avoir le coût d'opportunité le plus faible dans la production d'un bien par rapport à un autre pays",
                        "Produire plus rapidement que les autres pays",
                        "Avoir les travailleurs les mieux formés"
                    ],
                    correct: 1,
                    explication: "Un pays dispose d'un avantage comparatif dans la production du bien où il possède, relativement à l'autre pays, le coût d'opportunité le plus faible par rapport à la production de l'autre bien."
                },
                {
                    id: 5,
                    question: "Dans l'exemple du cours, si le Royaume-Uni met 1h pour produire du tissu et 8h pour du vin, quel est le coût d'opportunité d'une unité de tissu ?",
                    options: [
                        "8 unités de vin",
                        "1/8 unité de vin",
                        "1 unité de vin",
                        "4 unités de vin"
                    ],
                    correct: 1,
                    explication: "En 1h, on peut produire 1 unité de tissu OU 1/8 de vin. Le coût d'opportunité du tissu est donc 1/8 unité de vin (ce à quoi on renonce)."
                },
                {
                    id: 6,
                    question: "Aux États-Unis, lors de l'ouverture au commerce avec la Chine, qui sont les gagnants selon le modèle présenté ?",
                    options: [
                        "Les travailleurs non qualifiés",
                        "Les détenteurs de capital et les consommateurs",
                        "Tous les citoyens également",
                        "Les syndicats"
                    ],
                    correct: 1,
                    explication: "Aux USA, pays riche en capital, les gagnants sont les détenteurs de capital (facteur abondant) et les consommateurs. Les travailleurs (facteur rare) sont perdants."
                },
                {
                    id: 7,
                    question: "En Chine, quel facteur de production bénéficie de l'ouverture au commerce avec les USA ?",
                    options: [
                        "Le capital",
                        "Les détenteurs d'entreprises",
                        "Le travail",
                        "La technologie"
                    ],
                    correct: 2,
                    explication: "En Chine, pays abondamment doté en travail, ce sont les travailleurs qui gagnent à l'échange. La demande de travail augmente avec la spécialisation dans les biens intensifs en main-d'œuvre."
                },
                {
                    id: 8,
                    question: "Qu'est-ce que le 'maillon intermédiaire manquant' ?",
                    options: [
                        "L'absence d'industries moyennes",
                        "La disparition des emplois à salaire intermédiaire",
                        "Le manque de formation professionnelle",
                        "L'absence de syndicats"
                    ],
                    correct: 1,
                    explication: "Le maillon intermédiaire manquant désigne le phénomène où le nombre d'emplois à salaire faible et élevé augmente, tandis que les emplois à salaire intermédiaire se font de plus en plus rares."
                },
                {
                    id: 9,
                    question: "Quel est le trilemme de Rodrik ?",
                    options: [
                        "Croissance, emploi, inflation",
                        "Hypermondialisation, démocratie, souveraineté nationale",
                        "Liberté, égalité, fraternité",
                        "Production, consommation, épargne"
                    ],
                    correct: 1,
                    explication: "Selon Rodrik, il est impossible de satisfaire simultanément trois objectifs : l'hypermondialisation, la démocratie au sein des États-nations, et la souveraineté nationale."
                },
                {
                    id: 10,
                    question: "Comment mesure-t-on principalement l'intensité de la mondialisation ?",
                    options: [
                        "Uniquement par le volume des échanges",
                        "Par le volume des échanges ET la réduction des écarts de prix entre pays",
                        "Par le nombre de traités commerciaux",
                        "Par la croissance du PIB mondial"
                    ],
                    correct: 1,
                    explication: "Le cours présente deux méthodes : le volume des échanges (part des importations/exportations dans le PIB) et la réduction des écarts de prix entre pays exportateurs et importateurs."
                },
                {
                    id: 11,
                    question: "Dans un pays riche qui échange avec un pays pauvre, que se passe-t-il pour les travailleurs non qualifiés du pays riche ?",
                    options: [
                        "Ils gagnent grâce à de nouveaux emplois",
                        "Ils perdent car ils sont en concurrence avec le facteur abondant du pays pauvre",
                        "Leur situation ne change pas",
                        "Ils bénéficient de salaires plus élevés"
                    ],
                    correct: 1,
                    explication: "Dans le pays riche, les travailleurs non qualifiés perdent car ils sont en concurrence avec le facteur relativement abondant du pays pauvre, ce qui augmente les inégalités."
                },
                {
                    id: 12,
                    question: "Quelle a été l'évolution des inégalités au sein des pays entre 1980 et 2017 ?",
                    options: [
                        "Forte diminution",
                        "Stabilité ou hausse",
                        "Disparition complète",
                        "Légère baisse"
                    ],
                    correct: 1,
                    explication: "Le cours indique que de 1980 à 2017, on observe une stabilité ou une hausse des inégalités au sein des pays, notamment dans les pays anciennement industrialisés."
                }
            ];

            const [currentQuestion, setCurrentQuestion] = useState(0);
            const [selectedAnswer, setSelectedAnswer] = useState(null);
            const [showExplanation, setShowExplanation] = useState(false);
            const [score, setScore] = useState(0);
            const [answeredQuestions, setAnsweredQuestions] = useState([]);
            const [quizFinished, setQuizFinished] = useState(false);

            const handleAnswerClick = (index) => {
                if (selectedAnswer === null) {
                    setSelectedAnswer(index);
                    setShowExplanation(true);
                    
                    if (index === questions[currentQuestion].correct) {
                        setScore(score + 1);
                    }
                    
                    setAnsweredQuestions([...answeredQuestions, {
                        question: currentQuestion,
                        correct: index === questions[currentQuestion].correct
                    }]);
                }
            };

            const handleNextQuestion = () => {
                if (currentQuestion < questions.length - 1) {
                    setCurrentQuestion(currentQuestion + 1);
                    setSelectedAnswer(null);
                    setShowExplanation(false);
                } else {
                    setQuizFinished(true);
                }
            };

            const handleRestart = () => {
                setCurrentQuestion(0);
                setSelectedAnswer(null);
                setShowExplanation(false);
                setScore(0);
                setAnsweredQuestions([]);
                setQuizFinished(false);
            };

            const getScoreColor = () => {
                const percentage = (score / questions.length) * 100;
                if (percentage >= 80) return 'text-green-600';
                if (percentage >= 60) return 'text-blue-600';
                if (percentage >= 40) return 'text-orange-600';
                return 'text-red-600';
            };

            const getScoreMessage = () => {
                const percentage = (score / questions.length) * 100;
                if (percentage >= 80) return 'Excellent ! Vous maîtrisez parfaitement le cours.';
                if (percentage >= 60) return 'Bon travail ! Quelques révisions vous permettront de perfectionner vos connaissances.';
                if (percentage >= 40) return 'Pas mal, mais il faut encore travailler le cours.';
                return 'Il faut revoir le cours en profondeur.';
            };

            if (quizFinished) {
                return (
                    <div className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 p-8">
                        <div className="max-w-2xl mx-auto bg-white rounded-xl shadow-2xl p-8">
                            <div className="text-center">
                                <div className="text-yellow-500 mx-auto mb-6">
                                    <AwardIcon />
                                </div>
                                <h2 className="text-3xl font-bold text-gray-800 mb-4">QCM Terminé !</h2>
                                <div className={`text-6xl font-bold mb-4 ${getScoreColor()}`}>
                                    {score}/{questions.length}
                                </div>
                                <p className="text-xl text-gray-600 mb-8">{getScoreMessage()}</p>
                                
                                <div className="bg-gray-50 rounded-lg p-6 mb-8">
                                    <h3 className="font-semibold text-lg mb-4 text-gray-800">Résumé de vos réponses</h3>
                                    <div className="space-y-2">
                                        {answeredQuestions.map((answer, index) => (
                                            <div key={index} className="flex items-center justify-between p-2 bg-white rounded">
                                                <span className="text-gray-700">Question {index + 1}</span>
                                                {answer.correct ? (
                                                    <div className="text-green-500"><CheckIcon /></div>
                                                ) : (
                                                    <div className="text-red-500"><XIcon /></div>
                                                )}
                                            </div>
                                        ))}
                                    </div>
                                </div>

                                <button
                                    onClick={handleRestart}
                                    className="flex items-center justify-center gap-2 bg-blue-600 text-white px-8 py-3 rounded-lg hover:bg-blue-700 transition-colors mx-auto text-lg font-semibold"
                                >
                                    <RefreshIcon />
                                    Recommencer le QCM
                                </button>
                            </div>
                        </div>
                    </div>
                );
            }

            return (
                <div className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 p-4 md:p-8">
                    <div className="max-w-3xl mx-auto">
                        <div className="bg-white rounded-xl shadow-2xl p-6 md:p-8">
                            <div className="mb-6">
                                <div className="flex justify-between items-center mb-4">
                                    <h1 className="text-2xl md:text-3xl font-bold text-gray-800">
                                        Échanges et Mondialisation
                                    </h1>
                                    <div className="text-right">
                                        <div className="text-sm text-gray-500">Score</div>
                                        <div className="text-2xl font-bold text-blue-600">{score}/{answeredQuestions.length}</div>
                                    </div>
                                </div>
                                
                                <div className="flex items-center gap-2 text-sm text-gray-600 mb-4">
                                    <span className="font-semibold">Question {currentQuestion + 1}</span>
                                    <span className="text-gray-400">/</span>
                                    <span>{questions.length}</span>
                                </div>

                                <div className="w-full bg-gray-200 rounded-full h-2">
                                    <div 
                                        className="bg-blue-600 h-2 rounded-full transition-all duration-300"
                                        style={{ width: `${((currentQuestion + 1) / questions.length) * 100}%` }}
                                    />
                                </div>
                            </div>

                            <div className="mb-8">
                                <h2 className="text-xl md:text-2xl font-semibold text-gray-800 mb-6">
                                    {questions[currentQuestion].question}
                                </h2>

                                <div className="space-y-3">
                                    {questions[currentQuestion].options.map((option, index) => {
                                        let buttonClass = "w-full text-left p-4 rounded-lg border-2 transition-all ";
                                        
                                        if (selectedAnswer === null) {
                                            buttonClass += "border-gray-300 hover:border-blue-400 hover:bg-blue-50";
                                        } else if (index === questions[currentQuestion].correct) {
                                            buttonClass += "border-green-500 bg-green-50";
                                        } else if (index === selectedAnswer) {
                                            buttonClass += "border-red-500 bg-red-50";
                                        } else {
                                            buttonClass += "border-gray-300 opacity-50";
                                        }

                                        return (
                                            <button
                                                key={index}
                                                onClick={() => handleAnswerClick(index)}
                                                disabled={selectedAnswer !== null}
                                                className={buttonClass}
                                            >
                                                <div className="flex items-center justify-between">
                                                    <span className="text-gray-800">{option}</span>
                                                    {selectedAnswer !== null && index === questions[currentQuestion].correct && (
                                                        <div className="text-green-600"><CheckIcon /></div>
                                                    )}
                                                    {selectedAnswer === index && index !== questions[currentQuestion].correct && (
                                                        <div className="text-red-600"><XIcon /></div>
                                                    )}
                                                </div>
                                            </button>
                                        );
                                    })}
                                </div>
                            </div>

                            {showExplanation && (
                                <div className={`p-4 rounded-lg mb-6 ${
                                    selectedAnswer === questions[currentQuestion].correct 
                                        ? 'bg-green-50 border-2 border-green-200' 
                                        : 'bg-red-50 border-2 border-red-200'
                                }`}>
                                    <div className="flex items-start gap-3">
                                        {selectedAnswer === questions[currentQuestion].correct ? (
                                            <div className="text-green-600 flex-shrink-0 mt-1"><CheckIcon /></div>
                                        ) : (
                                            <div className="text-red-600 flex-shrink-0 mt-1"><XIcon /></div>
                                        )}
                                        <div>
                                            <p className="font-semibold text-gray-800 mb-2">
                                                {selectedAnswer === questions[currentQuestion].correct ? 'Correct !' : 'Incorrect'}
                                            </p>
                                            <p className="text-gray-700">{questions[currentQuestion].explication}</p>
                                        </div>
                                    </div>
                                </div>
                            )}

                            {showExplanation && (
                                <button
                                    onClick={handleNextQuestion}
                                    className="w-full bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 transition-colors font-semibold text-lg"
                                >
                                    {currentQuestion < questions.length - 1 ? 'Question suivante' : 'Voir les résultats'}
                                </button>
                            )}
                        </div>
                    </div>
                </div>
            );
        };

        ReactDOM.render(<QCMMondialisation />, document.getElementById('root'));
    </script>
</body>
</html>
