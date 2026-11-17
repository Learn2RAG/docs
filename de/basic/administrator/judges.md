---
layout: default
title: Judges
nav_order: 11
permalink: /de/basic/administrator/judges.html
parent: Administratorhandbuch
---

## Judges

Learn2RAG enthält zwei auf [RAGAS](https://docs.ragas.io/en/stable/) basierende Judges: den Context Relevance Judge und den Answer Relevance Judge.
Diese Judges erhöhen die Zuverlässigkeit der Pipeline, indem sie irrelevante Kontexte oder Antworten erkennen und Korrekturmaßnahmen auslösen, wenn ihre Relevanzbewertung unter einem konfigurierbaren Schwellenwert liegt.

### Context Relevance Judge

Der Context Relevance Judge (`context_relevance_judge`) prüft, ob die abgerufenen Kontexte Informationen enthalten, die für die Frage des Benutzers relevant sind. Er wird nach den Schritten Retrieval und Re-Ranking ausgeführt, bevor die Kontexte zur Antwortgenerierung an das Large Language Model (LLM) übergeben werden. Dieser Judge verwendet die RAGAS-Metrik Context Relevance, die die Relevanz der abgerufenen Kontexte mithilfe einer LLM-basierten Bewertung misst.

Der Judge vergibt eine Relevanzbewertung und vergleicht sie mit dem Schwellenwert. Erreicht oder überschreitet die Bewertung den Schwellenwert, werden die abgerufenen Kontexte zur Antwortgenerierung an das LLM übergeben. Andernfalls formuliert die Pipeline die Anfrage um und führt das Retrieval erneut durch, um relevantere Kontexte zu erhalten. Dieser erneute Versuch ist auf einen Durchlauf begrenzt, um wiederholte Retrieval-Vorgänge zu vermeiden. Liegt die Relevanzbewertung auch nach dem erneuten Versuch unter dem Schwellenwert, werden die neu abgerufenen Kontexte trotzdem an das LLM übergeben.

### Answer Relevance Judge

Der Answer Relevance Judge (`answer_relevance_judge`) prüft, ob die generierte Antwort die Frage des Benutzers angemessen beantwortet. Er wird ausgeführt, nachdem das LLM eine Antwort erzeugt hat und bevor diese an den Benutzer zurückgegeben wird. Dieser Judge verwendet die RAGAS-Metrik Answer Relevancy, die die semantische Übereinstimmung zwischen der generierten Antwort und der ursprünglichen Frage bewertet.

Der Judge vergibt eine Relevanzbewertung und vergleicht sie mit dem Schwellenwert. Erreicht oder überschreitet die Bewertung den Schwellenwert, wird die generierte Antwort an den Benutzer zurückgegeben. Andernfalls erzeugt die Pipeline anhand derselben abgerufenen Kontexte eine neue Antwort und gibt sie ohne erneute Relevanzbewertung an den Benutzer zurück. Auch dieser erneute Versuch ist auf einen Durchlauf begrenzt, um wiederholte Antwortgenerierungen zu vermeiden.

### Konfiguration

Beide Judges können über die Pipeline-Konfiguration unabhängig voneinander aktiviert oder deaktiviert werden. Sie verwenden einen gemeinsamen, konfigurierbaren Schwellenwert (`judge_threshold`), der festlegt, wann ein erneuter Versuch ausgelöst wird. Der Standardwert ist 0,7 und kann an die Anforderungen Ihrer Anwendung angepasst werden.

Standardmäßig sind beide Judges deaktiviert. Das folgende Beispiel aktiviert beide Judges mit dem Standardschwellenwert:

```json
{
    "context_relevance_judge": true,
    "answer_relevance_judge": true,
    "judge_threshold": 0.7
}
```
