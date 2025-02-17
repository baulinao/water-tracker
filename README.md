# water-track
package com.example.watertracker;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private int totalWaterConsumed = 0; // Общее количество выпитой воды
    private final int dailyGoal = 2000; // Цель по количеству воды (в мл)

    private TextView waterConsumedText;
    private TextView goalText;
    private Button addWaterButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Инициализация элементов интерфейса
        waterConsumedText = findViewById(R.id.waterConsumedText);
        goalText = findViewById(R.id.goalText);
        addWaterButton = findViewById(R.id.addWaterButton);

        // Отображение начальных данных
        updateUI();

        // Слушатель для кнопки добавления воды
        addWaterButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Добавляем 250 мл воды (можно настроить по вашему усмотрению)
                totalWaterConsumed += 250;
                updateUI();
            }
        });
    }

    // Обновляем интерфейс
    private void updateUI() {
        waterConsumedText.setText("Выпито воды: " + totalWaterConsumed + " мл");
        goalText.setText("Цель: " + dailyGoal + " мл");

        // Проверка на выполнение цели
        if (totalWaterConsumed >= dailyGoal) {
            goalText.setText("Цель достигнута! Молодец!");
        }
    }
}er
